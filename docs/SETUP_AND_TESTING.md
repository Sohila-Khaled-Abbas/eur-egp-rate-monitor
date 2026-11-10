# Setup and testing checklist

This guide expands the import instructions in the root README.

## Before import

- [ ] Confirm your n8n instance supports the nodes and Data Tables used by the export.
- [ ] Create an OpenRouter credential in n8n.
- [ ] Create a Telegram bot, add it to the destination chat, and keep its token in n8n Credentials.
- [ ] Create `EUR_EGP_Rate_State` with the three documented columns.

## After import

- [ ] Keep the workflow inactive while configuring it.
- [ ] In `Get Previous EUR-EGP Rates`, select your newly created `EUR_EGP_Rate_State` table.
- [ ] In `Update EUR-EGP Baseline`, select the same table.
- [ ] Replace the Telegram chat-ID placeholder.
- [ ] Select OpenRouter and Telegram credentials in their corresponding nodes.
- [ ] Confirm Schedule Trigger is every five minutes.
- [ ] Confirm workflow timezone is `Africa/Cairo`.
- [ ] Fetch and validate a current feed item, then seed the Data Table with actual rates.

## Test sequence

1. Run the fetch and extraction nodes. Verify that `currencyPair` is `EUR-EGP`, the two rates are numbers, and observation metadata exists.
2. Verify the baseline row contains the current rates and is keyed by `EUR-EGP`.
3. Test a change: temporarily replace the saved baseline with clearly different numeric values. Run the workflow and verify AI output, Telegram delivery, then updated baseline values.
4. Restore the baseline if the test run did not already update it. Do not leave artificial test rates in the table.
5. Test no change: run again with the same source values and baseline. The FALSE branch should end without a Telegram message or Data Table update.
6. Review the received message. Confirm the bank and rate labels use the correct customer direction.
7. Activate the workflow only after both branches pass and the baseline is real.

## Direction reference

- `youSellEurRate` / `youSellEurBank`: the bank buys EUR from the customer.
- `youBuyEurRate` / `youBuyEurBank`: the bank sells EUR to the customer.

Do not reverse these meanings when editing the AI prompt or the Telegram text.

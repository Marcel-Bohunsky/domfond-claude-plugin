# DomFond for Claude

DomFond answers questions about loans from the Slovak State Housing Development Fund (Štátny fond rozvoja bývania, ŠFRB) for renovating apartment buildings in Slovakia. It uses the same data and the same calculation as the public calculator on [domfond.sk](https://domfond.sk/kalkulacka).

DomFond is an independent application by [VisionEdge, s. r. o.](https://visionedge.sk) It is not affiliated with the fund and is not an official tool of the fund. The fund decides on every loan application.

## What this plugin contains

- **DomFond connector:** the remote MCP server `https://domfond.sk/mcp` with four read-only tools. It needs no account and no sign-in.
- **Skill `domfond-onboarding`:** explains what the DomFond application is and what it can do, using only the facts in the skill, and leads to the tools for loan questions.

## Tools

| Tool | What it returns |
|---|---|
| `get_loan_conditions` | The 2026 interest rate, loan limit, share of costs and maturity for each renovation purpose |
| `calculate_loan` | A loan estimate for a building: maximum loan for each purpose and in total, interest rate, monthly and annual payment and the part of the loan the fund may forgive |
| `get_application_window` | Whether the fund accepts applications today and when the yearly window (15 January to 31 August) opens or closes |
| `explain_term` | Explanations of Slovak terms such as SVB (association of flat owners) or list vlastníctva (ownership certificate) |

All four tools only read public data and calculate. They store nothing, call no other service and have no access to the data in the DomFond application.

## Setup

Install DomFond from the Claude directory, or add the connector yourself:

1. In Claude, open Customize, then Connectors, and choose Add custom connector.
2. Enter the name `DomFond` and the URL `https://domfond.sk/mcp`. No sign-in is needed.
3. In a chat, make sure the DomFond connector is turned on and ask a question about an ŠFRB loan.

## Example prompts

- What are the ŠFRB interest rates and loan limits for renovating an apartment building in 2026?
- Estimate the ŠFRB loan for insulating our block of flats: 3,000 m² of flats, works cost 600,000 EUR.
- Can we submit an ŠFRB loan application for our apartment building today?
- What does SVB mean for apartment buildings in Slovakia?

You can ask in Slovak or in English. Answers follow the 2026 conditions under Act No. 150/2013 Coll. and Decree No. 284/2013 Coll. as amended. They are estimates: the fund decides on every application, and the conditions for later years may change.

## Troubleshooting

- **The answer says there were too many requests** ("Príliš veľa požiadaviek z tejto adresy"): the server accepts at most 300 tool calls in 10 minutes from one address. Wait a few minutes and ask again.
- **Claude answers without the DomFond tools:** check that the DomFond connector is turned on in the chat, or mention DomFond in the question.
- **You need a check of the numbers or more help:** use the calculator on [domfond.sk](https://domfond.sk/kalkulacka) or contact us.

## Privacy

The plugin needs no name, contact details or other personal data. Inputs are used only to prepare the answer and are not stored. Details are in article 3.6 of the [DomFond privacy policy](https://domfond.sk/ochrana-osobnych-udajov#doplnok-claude).

## Support

- E-mail: [info@visionedge.sk](mailto:info@visionedge.sk)
- Help page in Slovak: [domfond.sk/pomoc](https://domfond.sk/pomoc)

## License

Copyright 2026 VisionEdge, s. r. o. All rights reserved. See [LICENSE](LICENSE).

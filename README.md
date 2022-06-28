# Aave's Risk Framework

{% hint style="info" %}
Aave holds security at its core with V3 audits by [Trail of Bits](https://github.com/aave/aave-v3-core/blob/master/audits/07-01-2022_TrailOfBits_AaveV3.pdf), [ABDK](https://github.com/aave/aave-v3-core/blob/master/audits/27-01-2022_ABDK_AaveV3.pdf), [Peckshield](https://github.com/aave/aave-v3-core/blob/master/audits/14-01-2022_PeckShield_AaveV3.pdf), [OpenZeppelin](https://github.com/aave/aave-v3-core/blob/master/audits/01-11-2021_OpenZeppelin_AaveV3.pdf), [SigmaPrime] and formal verification by [Certora](https://github.com/aave/aave-v3-core/blob/master/Certora/certora/Verification_Report.pdf) further detailed in Security & Audits.
{% endhint %}

Aave Protocol V3 introduces more sophisticated risk parameters and features to provide the protocol a high level of protection against potential insolvency. 👇🏻 is the list of new protocol _risk management_ additions
- Isolation mode assets
  Allows to list riskier assets in *Isolation*. Isolation mode restricts to:
  - only borrow isolated stablecoins
  - only use single isolated asset as collateral at a time

- Siloed assets
  Allows assets with potentially manipulatable oracle to be listed as supply-only i.e. cannot be used as collateral.

- New Permissioned Roles for `RISK_ADMIN`
  Aave Governance can now assign entities with permissioned role in the protocol. These entities can change risk parameters, if needed, without needing a governance vote for parameter update. This enables protocol to adjust risk parameters more efficiently and quickly as the market matures.

- Supply and Borrow caps
  Each asset reserve can now be (optional) configured to have upper bounds on supply and borrow. This helps in reducing exposure to certain assets and mitigates infinite minting or price oracle manipulation risks.

- Variable liquidation close factor
  In V3 liquidation mechanism has been improved to allow the position to be fully liquidated when it approaches insolvancy (HF < 0.95)

- Price Oracle sentinel
  The sentinal feature is mainly aimed for L2s to handle eventual downtime of the sequencers by introducing a grace period for liquidations and ability for `RISK_ADMINS` to disable borrowing for a reserve under specific circumstances.

The following documentation analyses the fundamental risks of the protocol and describes the processes in place to mitigate them in more details.

{% hint style="info" %}
If you have any questions, join the [Aave community Discord server](https://discord.gg/fVaDMqT); our team and members of the community look forward to helping you understand Aave's risks and risk management procedures.
{% endhint %}
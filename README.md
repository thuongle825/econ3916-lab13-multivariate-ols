# econ3916-lab13-multivariate-ols
# Multivariate OLS — What "Controlling For" Actually Does

## Objective
I used simulated data with a known truth to see what adding a control to a regression actually does: when it removes bias, when it creates bias, and how to check a regression table written by AI.

## Methodology
- Simulated wages that depend on education and an unobserved ability term, then ran a short regression (ability left out) and a long regression (ability in).
- Predicted the omitted-variable bias with the formula gamma × delta and compared it with the actual bias.
- Showed Frisch-Waugh-Lovell: I regressed education on ability and wages on ability, kept the residuals, and regressed one set of residuals on the other.
- Simulated a collider (c caused by both d and y, with no effect of d on y) and compared the regression with and without c as a control.
- Simulated two nearly identical regressors and used the variance inflation factor (VIF), the joint F-test and the sum of the coefficients to see what multicollinearity damages.
- Fitted an interaction between experience and union membership to let the return to experience differ between the two groups.
- Asked an AI to write a specification-table function, revised my prompt once, and checked its coefficients and standard errors against my own regressions.

## Key Findings
- Leaving ability out gave a return to education of 5,126 against a true 2,500. Putting it in gave 2,546.
- The bias formula predicted a bias of 2,629, and the actual bias was 2,626. Both terms were positive, so the short regression overstated the return.
- Regressing the part of wages that ability does not explain on the part of education that ability does not explain gave exactly the same coefficient as the full regression. "Controlling for" a variable means partialling it out.
- Controlling for the collider turned a true effect of zero into an estimate of −0.596, with a p-value that printed as 0.000. A control that is caused by both variables creates bias instead of removing it, and the regression output alone cannot show which case you are in.
- Multicollinearity made the standard errors about 12 times larger, but it did not bias the estimates: the two coefficients still added up to close to the true total.
- A year of experience was worth 903 to non-union workers and 504 to union members, so the union pay gap shrinks as experience grows.
- The AI's function matched my own coefficients and standard errors in every row. It also made a choice I never asked for, dropping missing rows separately for each specification, so I revised the prompt to drop them once so every row uses the same observations.

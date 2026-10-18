# Bellure Clinic — Team Website

**Assignment #5 — Forms and Validation (Part 1, teamwork)** · Group MT-2504

**Topic:** medical cosmetology clinic in Astana
**Live website:** https://aikonzhenisovvova-ops.github.io/bellure.clinic3/

## Team

| Member | GitHub | Page |
|---|---|---|
| Nurakysheva Ayaulym | `aikonzhenisovvova-ops` | `index.html` |
| Bekbolat Adina | `adinabek` | `services.html` |
| Nazymkyzy Aizada | `Aizzadamsn` | `about.html` |
| Khabibullina Aigerim | `aigerim-kh` | `contact.html` |

Each member's contribution is described in her own section of the report and in her commits.

## How to open

Extract the ZIP and open `contact.html` or `register.html` in any browser. No server or internet is needed: all paths are relative and Bootstrap 5.3.3 is stored in `vendor/bootstrap/`.

## Forms

| Page | Form | Rules |
|---|---|---|
| `contact.html` | Name, Email, Message, Submit | all `required`; `type="email"`; name `minlength="2"`; message `minlength="10"` and `maxlength="500"` |
| `register.html` | First name, Last name, Email, Password, Confirm password, Gender (optional), Interests (optional), Country, Submit, Reset | names `minlength="2"`; email `type="email"`; passwords `minlength="8"` and must match; country `required` with an empty default option |

- **Styling:** Bootstrap classes `form-label`, `form-control`, `form-select`, `form-text`, `form-check`, the grid (`row`, `col-md-6`) and `valid-feedback` / `invalid-feedback`.
- **Feedback:** `js/forms.js` checks the real value of each field and toggles `.is-valid` / `.is-invalid` on blur, while typing and on submit, with a message that matches the problem. The forms use `novalidate`, so Bootstrap feedback replaces the browser's pop-ups.
- **Password match:** HTML cannot compare two fields, so `forms.js` compares them and clears the error as soon as they agree.
- **Submit and Reset:** invalid input stops submission; valid input shows a demonstration message (nothing is sent or stored); Reset clears the data and all feedback.

## Test log

Tested in Chromium at 1280px and 375px; screenshots are in `screenshots/`.

| Case | Input | Expected | Actual |
|---|---|---|---|
| Empty required fields | Submit empty form | Required fields red, each with its own message, no success message | As expected |
| Invalid email | `aigerim@` | "Enter an email address like name@example.com." | As expected |
| Message length | `Hi there` (8) / 10 / 500 / 501 characters | 8 red; 10 and 500 green; 501 red | As expected (typing stops at 500; 501 tested by script) |
| Password too short | `short` | "Your password needs at least 8 characters." | As expected |
| Passwords differ | `password123` / `password124` | "The passwords do not match."; turns green when fixed | As expected |
| No country | Country left empty | "Please choose your country." | As expected |
| All valid | Sample valid data | All green, demonstration message shown | As expected |
| Reset after errors | Press "Reset form" | Empty form, no marks, no message | As expected |
| Mobile / desktop | 375px / 1280px | One column on phone, two columns on desktop, no sideways scrolling | As expected |

## Structure

```
index.html  services.html  about.html  contact.html  register.html
css/       style.css  responsive.css  forms.css
js/        forms.js
vendor/    bootstrap/
images/  fonts/  screenshots/
```

The forms are a demonstration only: no data is sent, stored or used to create an account.

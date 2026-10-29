# ប្រព័ន្ធគ្រប់គ្រងជំនួយបច្ចេកទេស (IT Helpdesk Portal)

ប្រព័ន្ធ Helpdesk សាងសង់ដោយប្រើប្រាស់ **Next.js 16**, **React 19**, **Tailwind CSS v4**, **Drizzle ORM** និង **PostgreSQL**។

## អ្វីដែលបានកែសម្រួលឲ្យដំណើរការឡើងវិញ (Fixes Applied)
1. **ដោះស្រាយបញ្ហា "Login មិនចូល" ទាំងស្រុង**៖
   - គាំទ្រទាំង **HTTP Cookie** (`SameSite=Lax` សម្រាប់ `http://localhost:3000`) និង **HTTPS Iframe Cookie** (`SameSite=None; Secure; Partitioned`) រួមជាមួយ **Bearer Token Fallback** ដូច្នេះ Login ដំណើរការគ្រប់ Browser ទាំងអស់។
   - គាំទ្រការចូលប្រើប្រាស់ដោយប្រើ **Email ឬ Username** (ឧ. `admin` ឬ `admin@helpdesk.com`)។
   - បម្លែងលេខខ្មែរ (`១២៣៤៥៦` -> `123456`) ដោយស្វ័យប្រវត្តិ ការពារករណីភ្លេចប្ដូរក្ដារចុចខ្មែរពេលវាយពាក្យសម្ងាត់។
2. **បង្កើត Database និងគណនីគំរូដោយស្វ័យប្រវត្តិ (`src/db/init.ts`)**៖
   - ភ្ជាប់ទៅ `postgresql://postgres:123456@127.0.0.1:5432/helpdesk` ដោយស្វ័យប្រវត្តិ (បើមិនទាន់មាន Database `helpdesk` ឬ Table ទេ ប្រព័ន្ធនឹងបង្កើតជូនដោយស្វ័យប្រវត្តិពេលដំណើរការដំបូង)។

## គណនីសម្រាប់ចូលប្រើប្រាស់ (Default Login Accounts)
| តួនាទី (Role) | Username | Email | Password |
| :--- | :--- | :--- | :--- |
| **Admin** | `admin` | `admin@helpdesk.com` | `123456` |
| **IT Agent** | `agent` | `agent@helpdesk.com` | `123456` |
| **Staff User** | `user` | `user@helpdesk.com` | `123456` |

## របៀបដំណើរការលើកុំព្យូទ័រផ្ទាល់ (Local Setup)
1. ត្រូវប្រាកដថា **PostgreSQL** កំពុងដំណើរការលើ Port `5432` (User: `postgres`, Password: `123456` ឬកែក្នុង `.env`)។
2. ដំឡើងកញ្ចប់បណ្ណាល័យ និងដំណើរការ៖
   ```bash
   npm install
   npm run dev
   ```
3. បើក Browser ទៅកាន់ `http://localhost:3000`។

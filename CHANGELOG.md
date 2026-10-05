# Svara change log (clinician)

Production-minded record. No secrets in this file. Times are IST.

## Environment
- Front end: static single-file app, GitHub Pages, repo jairulez/svara-clinician, branch main, file index.html
- Backend: Supabase free project "svara" (ref epedefnrawpwdbbkyopc, region ap-northeast-1 Tokyo). Anon key is public by design and embedded in index.html. Service-role key is not stored anywhere.
- Sibling repos: jairulez/svara (customer), jairulez/svara-clinician, jairulez/svara-admin
- Status: TEST ENVIRONMENT. Test accounts only. Not open to real users. Not medical advice.

## v0.1.0 - 2026-10-05
- Created repos, enabled Pages (deploy from main).
- Supabase schema applied: 15 tables with row-level security (profiles, consents, snapshots, checkins, safety_events, access_log, clinician_shares, clinician_notes, questions, routines, claim_rules, products, content, audit_log, feature_flags), functions my_role, is_shared_with_me, handle_new_user, guard_role, delete_my_account, list_clinicians, admin_stats, log_audit. Seeds: 10 questions, 7 routines, 8 claim rules, 3 sample products (inactive, unsellable), 4 content items, 4 feature flags.
- Auth: email+password, email confirmation off (test only).
- Added access_log insert policy (al_ins) so people and clinicians can write access entries.
- Test accounts created: customer, clinician, admin (credentials in the owner's vault, passwords set by the owner).
- Tested: cross-user reads/writes blocked, role self-promotion blocked, admin functions refuse non-admins, clinician sees data only during an active share, account delete works.

## Rollback
- Front end: revert the commit in this repo (GitHub: commit page > Revert) or unpublish Pages in Settings > Pages.
- Database: schema SQL is kept by the build agent; to undo a policy run "drop policy al_ins on access_log". To stop everything, pause the Supabase project.

## Known limits
- Supabase free projects pause after about 7 days of no activity.
- Not tested on a physical phone.
- Legal review, DPDP duties and opening to real users are the owner's decision.

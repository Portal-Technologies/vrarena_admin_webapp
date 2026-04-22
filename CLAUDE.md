# vrarena_admin_webapp — Build artifact (не редактировать!)

- **Домен:** loyalty
- **Стек:** статический web-билд (автогенерируется из Flutter-проекта)
- **Supabase:** — (runtime коннектится к `kzdxitunulgdoorbkqdw`)
- **Заменяет (из old/):** —
- **Docs:** [README.md](README.md)
- **Open issues:** [TASKS.md](TASKS.md)

## ⚠ Не редактировать вручную

Это **публичный GitHub-репо**, в который **автоматически** пушится web-билд админки операторов из [../portal_admin_app_ff/](../portal_admin_app_ff/CLAUDE.md). Vercel подключён к этому репо и деплоит его как статику.

Любые правки здесь будут **перезаписаны** следующим запуском `deploy_web.sh` из [portal_admin_app_ff/](../portal_admin_app_ff/CLAUDE.md).

## Что делать, если нужны изменения в web-админке

1. Открыть **[loyalty/portal_admin_app_ff/](../portal_admin_app_ff/CLAUDE.md)** (исходный Flutter проект).
2. Внести изменения через FlutterFlow или в `lib/custom_code/`.
3. Запустить `deploy_web.sh` (из корня `portal_admin_app_ff/`).
4. Скрипт собирает Flutter web (`flutter build web`) и пушит в этот репо.
5. Vercel автодеплоит.

## Почему репо публичный

Vercel в бесплатном плане требует public repo для некоторых интеграций. Суть web-билда — статический HTML/JS без секретов в исходниках (секреты в runtime env vars Supabase, доступ через auth).

⚠ Следить, чтобы никакие **ключи** (service_role, закрытые FUNCTION_SECRET) **не попадали в билд**. Admin app использует только `SUPABASE_URL` + anon key, которые публичны по дизайну.

## Связи

- **Источник:** [loyalty/portal_admin_app_ff/](../portal_admin_app_ff/CLAUDE.md).
- **Deploy target:** Vercel (настроен на ветку `main` этого репо).
- **Runtime backend:** `kzdxitunulgdoorbkqdw` (supabase-rus).

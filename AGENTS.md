# vrarena_admin_webapp — International operator admin (planned)

- **Домен:** loyalty
- **Стек:** планируется — статический web-билд Flutter (вероятно из клона/форка `portal_admin_app_ff`)
- **Supabase:** будет международный loyalty-сервис (пока не развёрнут)
- **Заменяет (из old/):** —
- **Docs:** [README.md](README.md)
- **Open issues:** [TASKS.md](TASKS.md) (локально, в public git игнорится)

## Назначение (future)

Этот публичный репозиторий будет использоваться для **международной версии** приложения для операторов VR-клубов Portal VR / ARMA. Международная версия:

- Будет смотреть на **международный сервис лояльности** (отдельный Supabase-инстанс, пока не развёрнут — не путать с RU `kzdxitunulgdoorbkqdw`).
- Публичный репо + Vercel-деплой остаются как инфраструктура (public требуется Vercel'ом на free plan).
- Источник Flutter-кода — вероятно клон / форк / ветка [portal_admin_app_ff/](../portal_admin_app_ff/CLAUDE.md) с адаптированными `environment.json` и, возможно, i18n-дефолтами.

## Текущее состояние (2026-04-23)

- Репо **заморожен** с 2026-04-10 — последний автодеплой-коммит `493664e`.
- RU-админка перешла на VPS-деплой через [portal_admin_app_ff/deploy_ru.sh](../portal_admin_app_ff/deploy_ru.sh) → `178.154.243.25:/data/www/operator-admin/` → `operator.partner.portal-vr.tech`.
- Скрипт `deploy_web.sh`, который ранее пушил сюда RU-билды, удалён в коммите `0bac817`.
- Vercel-интеграция (если ещё активна) показывает устаревший билд.

## Будущее использование

Когда международный сервис лояльности будет готов:

1. Решить источник кода: отдельный Flutter-репо / ветка `portal_admin_app_ff` (`international`?) / форк.
2. Создать новый deploy-скрипт (по образцу удалённого `deploy_web.sh`, но параметризованный под международный Supabase URL).
3. Настроить Vercel-проект на этот репо, задать env-переменные (если будут) на стороне Vercel.
4. Пройтись по i18n: возможно, RU убрать из дефолтного набора языков для international-сборки.

## Замечания

- `CLAUDE.md` и `TASKS.md` **не коммитятся в этот public repo** (занесены в `.gitignore`) — это рабочие заметки, не код.
- Ключи: в билде никогда не должно быть service_role / FUNCTION_SECRET. Только `SUPABASE_URL` + anon key (публичны по дизайну).

# Sugester API

Opis jak zintegrować własną aplikację lub serwis z systemem <http://sugester.pl/>


Dzięki API można z innych systemów dodawać posty/sugestie/błędy itp

## Spis treści
+ [API Token](#token)  
+ [Faktury - przykłady wywołania](#examples)  
	+ Dodanie nowej sugestii
+ [Post - specyfikacja](#post)


<a name="token"/>
##API token

Kod autoryzacyjny API (`API_TOKEN`) należy pobrać z ustawień aplikacji w menu: Ustawienia > API > Kod autoryzacyjny API. Dzięku niemu w wywołaniach API nie trzeba będzie podawać swojego loginu/hasła.

<a name="examples"/>
##Przykłady wywołania

Dodanie posta o typie "błąd":

```shell
curl http://your-prefix.sugester.pl/app/posts.json \
     -H 'Accept: application/json' \
     -H 'Content-Type: application/json' \
     -d '
{
"api_token": "API_TOKEN", 
"post": {
    "title":"post title2", 
    "content": "post content 2",
    "kind": "error"
  }
}'
```


<a name="post"/>
##Specyfikacja pól obiektu Post (Sugestia/Zgłoszenie/E-mail)

```shell
{
    "id": id posta
    "title": tytuł 
    "content": treść
    "kind": rodzaj sugestii ('suggestion', 'error', 'question', 'praise', 'private'),
    "user_id": id usera
    "points": liczba punktów
    "nick": nick usera
    "votes_cache": ilość oddanych głosów
    "comments_cache": ilość oddanych komentarzy
    "forum_id": id forum
    "category_id": id category
    "created_at": czas utworzenia
    "updated_at": czas ostatniej modyfikacji
    "ip": ip z którego oddano post
    "agent": info o przeglądarce
    "response": odpowiedź główna
    "response_user_id": id osoby która odpowiedziała
    "referrer": refferer
    "responsible_id": id przypisanej osoby
    "last_action_status": status ("created"),
    "email": email nadawcy
    "uid": token użytkownika,
    "spam_kind": rodzaj spamu,
    "answer": odpowiedz,
    "answered": czy jest odpowiedz,
    "duplicate_from_id": id duplikatu,
    "abstract": abstrakt,
    "status_id": id status,
    "view_count": ilość wyświetleń,
    "tags": tagi,
    "facebook_likes": ilość like facebokoowych,
    "min_votes_to_start": ilość głosów do rozpoczęcia prac,
    "use_html": czy html,
    "email_to": adres email do,
    "email_cc": adres email cc,
    "email_bcc": adres email bcc,
    "spam_score": scoring spamowy,
    "spam_report": info o spamie,
    "closed": czy zamkniete (true/false),
    "scheduled_at": przypisana data wykonania,
    "task_kind": rodzaj zadania ('feedback', 'email', 'task', 'help', 'chat', 'phone', 'lead', 'error', 'idea'),
    "priority": priorytet,
    "title_note": null,
    "user_spam_report": zgłoszenie spamu,
    "client_id": id klienta,
    "project_id": id projektu,
    "help_link": klucz linka pomocy,
    "help_content": treść pomocy,
    "post_id": id postu nadrzędnego,
    "www": strona www dodajacego post,
    "private": czy prywatny (true/false),
    "unread": czy nie przeczytany (true/false),
    "email_recipient": do kogo jest dany post (uzywane w helpdesk/mail),
    "email_reply_to": reply to  (uzywane w helpdesk/mail)
}
```


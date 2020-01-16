---
title: Omówienie rozszerzonej ochrony uwierzytelniania
ms.date: 03/30/2017
ms.assetid: 3d2ceffe-a7bf-4bd9-a5a2-9406423bd7f8
ms.openlocfilehash: 400bf7987b5fcd4ec75628d19a30739dd5f23b08
ms.sourcegitcommit: c01c18755bb7b0f82c7232314ccf7955ea7834db
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/15/2020
ms.locfileid: "75964599"
---
# <a name="extended-protection-for-authentication-overview"></a>Omówienie rozszerzonej ochrony uwierzytelniania
Ochrona rozszerzona uwierzytelniania pomaga chronić przed atakami typu man-in-the-Middle (MITM), w których osoba atakująca przechwytuje poświadczenia klienta i przekazuje je do serwera.  
  
 Rozważmy scenariusz od trzech uczestników: klient, serwer i osoba atakująca. Na serwerze znajduje się adres URL `https://server`, podczas gdy osoba atakująca ma `https://attacker`URL. Osoba atakująca uzyskuje dostęp do osoby atakującej, tak jakby była serwerem. Następnie osoba atakująca wysyła żądanie do serwera. Jeśli osoba atakująca próbuje uzyskać dostęp do bezpiecznego zasobu, serwer odpowie do osoby atakującej za pomocą nagłówka WWW-Authenticate. Osoba atakująca nie ma informacji o uwierzytelnianiu, więc wysyła do klienta nagłówek WWW-Authentication. Klient wysyła nagłówek autoryzacji do osoby atakującej, a osoba atakująca wysyła nagłówek na serwer i uzyskuje dostęp do bezpiecznych zasobów przy użyciu poświadczeń klienta.  
  
 Obecnie, gdy aplikacja kliencka uwierzytelnia się na serwerze przy użyciu protokołu Kerberos, Digest lub NTLM przy użyciu protokołu HTTPS, najpierw zostaje ustanowiony kanał zabezpieczenia na poziomie transportu (TLS), a uwierzytelnianie odbywa się przy użyciu tego kanału. Nie ma jednak powiązania między kluczem sesji wygenerowanym przez SSL (SSL) i kluczem sesji, który jest generowany podczas uwierzytelniania. Tak więc w poprzednim scenariuszu, Jeśli komunikacja odbywa się za pośrednictwem protokołu TLS (na przykład kanału HTTPS), istnieją dwa kanały SSL: jeden między klientem a atakującym, a drugi między intruziem a serwerem. Poświadczenia klienta są wysyłane z klienta na serwer najpierw za pośrednictwem kanału SSL między klientem a osobą atakującą, a następnie przez kanał między osobą atakującą a serwerem. Gdy poświadczenia klienta docierają do serwera, serwer weryfikuje poświadczenia bez wykrywania, czy kanał, w którym te poświadczenia zostały wysłane, pochodzi od osoby atakującej, a nie do klienta programu.  
  
 Rozwiązaniem jest użycie kanału zewnętrznego zabezpieczonego protokołem TLS i kanału wewnętrznego uwierzytelnionego przez klienta oraz przekazanie tokenu powiązania kanału (CBT) do serwera. CBT jest właściwością kanału zewnętrznego zabezpieczonego protokołem TLS i służy do powiązania zewnętrznego kanału z konwersacją za pośrednictwem kanału wewnętrznego uwierzytelnionego przez klienta.  
  
 W poprzednim scenariuszu CBT kanału protokołu TLS osoby atakującej klienta jest scalany z informacjami o autoryzacji wysyłanymi do serwera. Serwer z CBTą porównuje CBT zawarte w informacjach o uwierzytelnianiu klienta, który odnosi się do kanału atakującego klienta, do CBT dołączonego do kanału osoby atakującej-serwer. CBT jest specyficzny dla miejsca docelowego kanału, dlatego klient-osoba atakująca CBT nie jest zgodna z CBTem osoby atakującej — serwer. Dzięki temu serwer wykrywa atak MITM i odrzuca żądanie uwierzytelnienia.  
  
 Po stronie klienta nie jest wymagane żadne ustawienie konfiguracji. Po zaktualizowaniu klienta programu w celu przekazania CBT do serwera zawsze jest to możliwe. Jeśli serwer został również zaktualizowany, można go skonfigurować tak, aby korzystał z CBT lub go zignorować. Jeśli nie została zaktualizowana, zignoruje ją.  
  
 Serwer może mieć następujące poziomy ochrony:  
  
- Brak. Nie jest przeprowadzana Walidacja powiązań kanałów. Jest to zachowanie wszystkich serwerów, które nie zostały zaktualizowane.  
  
- Uwzględnieni. Wszystkie zaktualizowane komputery klienckie muszą podawać informacje o powiązaniu kanału z serwerem. Klienci, którzy nie zostali zaktualizowani, nie muszą tego robić. Jest to pośrednia opcja, która umożliwia zgodność aplikacji.  
  
- Szczegółowe. Wszyscy klienci muszą podawać informacje o powiązaniu kanału. Serwer odrzuca żądania uwierzytelniania pochodzące od klientów, które ich nie wykonują.  
  
 Aby uzyskać więcej informacji, zobacz przykład Win7 CBT/Extended Protection.  
  
## <a name="see-also"></a>Zobacz także

- [Model zabezpieczeń dla sieci szkieletowej aplikacji systemu Windows Server](https://docs.microsoft.com/previous-versions/appfabric/ee677202(v=azure.10))

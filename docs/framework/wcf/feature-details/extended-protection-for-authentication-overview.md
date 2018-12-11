---
title: Omówienie rozszerzonej ochrony uwierzytelniania
ms.date: 03/30/2017
ms.assetid: 3d2ceffe-a7bf-4bd9-a5a2-9406423bd7f8
ms.openlocfilehash: 6063aa7093ed6c70e835364fdf5dd1c4293dd2eb
ms.sourcegitcommit: ccd8c36b0d74d99291d41aceb14cf98d74dc9d2b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/10/2018
ms.locfileid: "53149747"
---
# <a name="extended-protection-for-authentication-overview"></a>Omówienie rozszerzonej ochrony uwierzytelniania
Rozszerzona ochrona uwierzytelniania pomaga w ochronie przed ataków typu man-in--middle (MITM) ataków, w których osoba atakująca przechwytuje poświadczenia klienta i przekazuje je do serwera.  
  
 Rozważmy scenariusz, za pomocą trzech uczestników: klienta, serwera i osoby atakującej. Serwer nie ma adresu URL `https://server`, podczas gdy osoba atakująca ma adres URL `https://attacker`. Osoba atakująca wskazówki klienta do uzyskiwania dostępu do osoba atakująca, tak jakby serwera. Osoba atakująca wysyła następnie żądanie do serwera. Jeśli osoba atakująca próbuje uzyskać dostęp do bezpiecznych zasobów, serwer odpowiada na osoba atakująca przy użyciu nagłówka WWW-Authenticate. Osoba atakująca nie ma informacje o uwierzytelnianiu, dlatego wysyła nagłówka WWW-Authenticate do klienta. Klient wysyła nagłówek autoryzacji dla osoby atakującej, a osoba atakująca wysyła nagłówek na serwerze i uzyskuje dostęp do bezpiecznych zasobów przy użyciu poświadczeń klienta.  
  
 Obecnie gdy aplikacja kliencka uwierzytelnia na serwerze przy użyciu protokołu Kerberos, szyfrowane lub NTLM przy użyciu protokołu HTTPS, ustanawiania kanału zabezpieczeń TLS (Transport Level) i uwierzytelnianie odbywa się za pomocą tego kanału. Jednakże nie istnieje żadne powiązanie między kluczem sesji, generowane przez Secure Sockets Layer (SSL) i klucza sesji, który jest generowany podczas uwierzytelniania. Dlatego w poprzednim scenariuszu komunikacja trwa miejsca za pośrednictwem protokołu TLS (na przykład kanału protokołu HTTPS), czy dwa kanały protokołu SSL utworzony: jednego między klientem i osoba atakująca i innym między osoba atakująca a serwerem. Poświadczenia klienta są wysyłane z klienta do serwera najpierw za pośrednictwem kanału SSL między klientem a osoba atakująca, a następnie za pośrednictwem kanału między osoba atakująca a serwerem. Gdy poświadczenia klienta dociera do serwera, serwer sprawdza poświadczenia bez wykrycia, że kanał, przez który te poświadczenia zostały wysłane pochodzi z osoba atakująca, a nie klient.  
  
 To rozwiązanie jest zewnętrzne kanału zabezpieczonego protokołem TLS i klient uwierzytelniony kanału wewnętrzny i przekazać kanału powiązanie Token (CBT) do serwera. CBT jest właściwością zewnętrzne kanału zabezpieczonego protokołem TLS i służy do tworzenia powiązania zewnętrzne kanału do konwersacji za pośrednictwem kanału wewnętrzny uwierzytelnienia klienta.  
  
 W poprzednim scenariuszu CBT kanału TLS osoba atakująca klienta jest scalany z informacji o autoryzacji, które są wysyłane do serwera. Serwera obsługująca CBT porównuje CBT zawarte w informacje uwierzytelniania klienta, które odnosi się do kanału osoba atakująca klienta, CBT dołączony do kanału, osoba atakująca serwera. CBT dotyczy kanału miejsca docelowego, więc klienta — osoba atakująca CBT jest niezgodna z serwera atakującej CBT. Dzięki temu serwer wykrywać ataki MITM i odmowy żądania uwierzytelnienia.  
  
 Po stronie klienta nie wymaga żadnych ustawień konfiguracji. Gdy klient został zaktualizowany do przekazania na serwer CBT, zawsze robi. Jeśli serwer został także zaktualizowany, można skonfigurować do używania CBT lub go zignorować. Jeśli nie został zaktualizowany, ignoruje go.  
  
 Serwer może mieć następujące poziomy ochrony:  
  
-   Brak. Odbywa się nie sprawdzenia poprawności powiązania kanału. Jest to zachowanie w procentach wszystkich serwerów, które nie zostały zaktualizowane.  
  
-   Częściowe. Wszyscy klienci, które zostały zaktualizowane, musisz podać informacje o powiązaniu kanału do serwera. Klienci, którzy nie zostały zaktualizowane nie trzeba to zrobić. Jest to opcja pośredniego, umożliwiający zgodności aplikacji.  
  
-   Pełna. Wszyscy klienci, musisz podać informacje o powiązaniu do kanału. Serwer odrzuca żądania uwierzytelniania od klientów, które to robi.  
  
 Aby uzyskać więcej informacji zobacz przykład Win7 CBT/rozszerzonej ochrony.  
  
## <a name="see-also"></a>Zobacz też  
 [Model zabezpieczeń dla systemu Windows Server AppFabric](https://go.microsoft.com/fwlink/?LinkID=201279&clcid=0x409)

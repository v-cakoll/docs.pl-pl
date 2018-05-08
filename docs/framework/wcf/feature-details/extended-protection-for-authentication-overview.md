---
title: Omówienie rozszerzonej ochrony uwierzytelniania
ms.date: 03/30/2017
ms.assetid: 3d2ceffe-a7bf-4bd9-a5a2-9406423bd7f8
author: BrucePerlerMS
manager: mbaldwin
ms.openlocfilehash: fdf18564d3545e0061d8323e544aecfeed621d0c
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="extended-protection-for-authentication-overview"></a>Omówienie rozszerzonej ochrony uwierzytelniania
Rozszerzona ochrona uwierzytelniania pomaga w ochronie przed man-in--middle (MITM) ataków, w których osoba atakująca przechwytuje poświadczenia klienta i przekazuje je do serwera.  
  
 Rozważmy scenariusz z trzech uczestników: klienta, serwera i osoby atakującej. Serwer nie ma adresu URL `https://server`, osoba atakująca ma adres URL `https://attacker`. Osoba atakująca sztuczki klienta do uzyskiwania dostępu do osoba atakująca, tak jakby był on serwera. Osoba atakująca następnie wysyła żądanie do serwera. Jeśli osoba atakująca próbuje uzyskać dostęp do bezpiecznego zasobu, serwer odpowiedzi dla osoby atakującej z nagłówka WWW-Authenticate. Osoba atakująca nie ma informacji o uwierzytelnianiu, więc wysyła klientowi nagłówka WWW-Authenticate. Klient wysyła nagłówek autoryzacji dla osoby atakującej, a osoba atakująca wysyła nagłówka do serwera i uzyskuje dostęp do bezpiecznych zasobów przy użyciu poświadczeń klienta.  
  
 Obecnie gdy aplikacja kliencka uwierzytelnia na serwerze przy użyciu protokołu Kerberos, szyfrowane lub NTLM przy użyciu protokołu HTTPS, najpierw nawiązaniu kanał zabezpieczeń TLS (Transport Level) i uwierzytelnianie odbywa się przy użyciu tego kanału. Jednakże nie istnieje żadne powiązanie między kluczem sesji generowane przez Secure Sockets Layer (SSL) i klucz sesji, który jest generowany podczas uwierzytelniania. Tak, w poprzednim scenariuszu, jeśli komunikacja przejmuje miejsca TLS (na przykład kanał HTTPS), istnieją dwa kanały SSL utworzony: jeden między klientem i osoba atakująca i inny między osoba atakująca a serwerem. Poświadczenia klienta są wysyłane z klienta do serwera najpierw za pośrednictwem kanału SSL między klientem a osoba atakująca, a następnie przez kanał między osoba atakująca a serwerem. Po poświadczenia klienta uzyskać dostęp do serwera, serwer sprawdza poświadczenia bez wykrycia, czy kanał, przez który te poświadczenia zostały wysłane pochodzi z osoba atakująca, a nie przez klienta.  
  
 Rozwiązaniem jest użycie zewnętrznego kanału zabezpieczonego protokołem TLS i kanał wewnętrzny uwierzytelnienia klienta oraz do przekazania kanału powiązanie Token (CBT) na serwerze. CBT jest właściwością zewnętrzne kanału zabezpieczonego protokołem TLS i jest używana do powiązania zewnętrzne kanału do konwersacji za pośrednictwem kanału wewnętrzny uwierzytelnienia klienta.  
  
 W poprzednim scenariuszu CBT kanału TLS osoba atakująca klienta jest scalany z informacji o autoryzacji, które są wysyłane do serwera. Serwer obsługujący CBT porównuje CBT zawarte w informacjach uwierzytelniania klienta, co odpowiada kanału klienta atakująca, CBT podłączonych do kanału serwera atakującej. CBT jest specyficzne dla docelowego kanału, więc atakująca klienta CBT jest niezgodny z serwera atakującej CBT. Dzięki temu serwer wykrycie ataku MITM i odmowy żądania uwierzytelnienia.  
  
 Po stronie klienta nie wymaga żadnych ustawień konfiguracji. Gdy klient został zaktualizowany do przekazania CBT do serwera, zawsze robi to. Jeśli serwer również została zaktualizowana, można skonfigurować użycie CBT lub ją zignorować. Jeśli nie został zaktualizowany, zignoruje ją.  
  
 Serwer może mieć następujące poziomy ochrony:  
  
-   Brak. Weryfikacja powiązania kanału, nie jest przeprowadzana. Jest to zachowanie wszystkich serwerów, które nie zostały zaktualizowane.  
  
-   Częściowe. Wszystkich klientów, które zostały zaktualizowane, musisz podać informacje o powiązaniu kanału do serwera. W tym celu nie masz klientów, które nie zostały zaktualizowane. Jest to pośredni opcja umożliwiająca zgodności aplikacji.  
  
-   Pełna. Wszyscy klienci podać informacje o powiązaniu kanału. Serwer odrzuca żądania uwierzytelniania od klientów, którzy nie zostanie.  
  
 Aby uzyskać więcej informacji zobacz przykład Win7 CBT/rozszerzonej ochrony.  
  
## <a name="see-also"></a>Zobacz też  
 [Model zabezpieczeń systemu Windows Server AppFabric](http://go.microsoft.com/fwlink/?LinkID=201279&clcid=0x409)

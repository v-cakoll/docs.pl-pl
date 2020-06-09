---
title: Opis uwierzytelniania HTTP
ms.date: 03/30/2017
ms.assetid: 9376309a-39e3-4819-b47b-a73982b57620
ms.openlocfilehash: a31c9f96185364c59dca1ff26251a30f5d7a88bc
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/09/2020
ms.locfileid: "84595092"
---
# <a name="understanding-http-authentication"></a>Opis uwierzytelniania HTTP
Uwierzytelnianie to proces identyfikacji, czy klient ma uprawnienia dostępu do zasobu. Protokół HTTP obsługuje uwierzytelnianie jako środek negocjowania dostępu do bezpiecznego zasobu.  
  
 Początkowe żądanie od klienta to zwykle żądanie anonimowe, które nie zawiera informacji o uwierzytelnianiu. Aplikacje serwera HTTP mogą odrzucać żądanie anonimowe, wskazując, że uwierzytelnianie jest wymagane. Aplikacja serwerowa wysyła nagłówki uwierzytelniania WWW, aby wskazać obsługiwane schematy uwierzytelniania. W tym dokumencie opisano kilka schematów uwierzytelniania dla protokołu HTTP i omówiono ich obsługę w programie Windows Communication Foundation (WCF).  
  
## <a name="http-authentication-schemes"></a>Schematy uwierzytelniania HTTP  
 Serwer może określić wiele schematów uwierzytelniania do wyboru dla klienta. W poniższej tabeli opisano niektóre ze schematów uwierzytelniania często dostępnych w aplikacjach systemu Windows.  
  
|Schemat uwierzytelniania|Opis|  
|---------------------------|-----------------|  
|Anonimowe|Żądanie anonimowe nie zawiera żadnych informacji o uwierzytelnianiu. Jest to równoznaczne z przyznaniem wszystkim dostępu do zasobu.|  
|Podstawowa|Uwierzytelnianie podstawowe wysyła ciąg szyfrowany algorytmem Base64, który zawiera nazwę użytkownika i hasło dla klienta. Algorytm Base64 nie jest formą szyfrowania i powinien być uważany za taki sam jak w przypadku wysyłania nazwy użytkownika i hasła w postaci zwykłego tekstu. Jeśli zasób musi być chroniony, zdecydowanie Rozważ użycie schematu uwierzytelniania innego niż uwierzytelnianie podstawowe.|  
|Szyfrowane|Uwierzytelnianie szyfrowane to schemat odpowiedzi na wyzwanie, który służy do zastępowania uwierzytelniania podstawowego. Serwer wysyła ciąg losowych danych o nazwie identyfikator *jednorazowy* do klienta jako wyzwanie. Klient odpowiada za pomocą skrótu, który zawiera nazwę użytkownika, hasło i identyfikator jednorazowy, wśród dodatkowych informacji. Złożoność tej wymiany wprowadza i wyznaczania wartości skrótu danych utrudniają kradzież i ponowne użycie poświadczeń użytkownika przy użyciu tego schematu uwierzytelniania.<br /><br /> Uwierzytelnianie szyfrowane wymaga używania kont domeny systemu Windows. *Obszar* podsumowania to nazwa domeny systemu Windows. W związku z tym nie można używać serwera z systemem operacyjnym, który nie obsługuje domen systemu Windows, takich jak Windows XP Home Edition, z uwierzytelnianiem szyfrowanym. Z drugiej strony, gdy klient jest uruchomiony w systemie operacyjnym, który nie obsługuje domen systemu Windows, konto domeny musi być jawnie określone podczas uwierzytelniania.|  
|NTLM|Uwierzytelnianie przy użyciu programu NT LAN Manager (NTLM) to schemat odpowiedzi na wyzwanie, który jest odmianą uwierzytelniania szyfrowanego. Protokół NTLM używa poświadczeń systemu Windows do przekształcania danych wyzwania zamiast niezaszyfrowanej nazwy użytkownika i hasła. Uwierzytelnianie NTLM wymaga wielu wymian między klientem a serwerem. Serwer i wszystkie pośredniczące serwery proxy muszą obsługiwać trwałe połączenia, aby pomyślnie zakończyć uwierzytelnianie.|  
|Negotiate|Uwierzytelnianie negocjowane automatycznie wybiera między protokołem Kerberos a uwierzytelnianiem NTLM, w zależności od dostępności. Protokół Kerberos jest używany, jeśli jest dostępny; w przeciwnym razie zostanie podjęta próba uwierzytelniania NTLM. Uwierzytelnianie Kerberos znacznie zwiększa się po NTLM. Uwierzytelnianie Kerberos jest jednocześnie szybsze niż NTLM i umożliwia wzajemne uwierzytelnianie i Delegowanie poświadczeń do komputerów zdalnych.|  
|Windows Live ID|Podstawowa usługa HTTP systemu Windows obejmuje uwierzytelnianie przy użyciu protokołów federacyjnych. Jednak standardowe transporty HTTP w programie WCF nie obsługują użycia federacyjnych schematów uwierzytelniania, takich jak Microsoft Windows Live ID. Obsługa tej funkcji jest obecnie dostępna za pomocą zabezpieczeń komunikatów. Aby uzyskać więcej informacji, zobacz [federacyjne i wystawione tokeny](federation-and-issued-tokens.md).|  
  
## <a name="choosing-an-authentication-scheme"></a>Wybieranie schematu uwierzytelniania  
 Podczas wybierania potencjalnych schematów uwierzytelniania dla serwera HTTP należy wziąć pod uwagę następujące zagadnienia:  
  
- Zastanów się, czy zasób musi być chroniony. Użycie uwierzytelniania HTTP wymaga przesłania większej ilości danych i może ograniczyć współdziałanie z klientami. Zezwalaj na anonimowy dostęp do zasobów, które nie muszą być chronione.  
  
- Jeśli zasób musi być chroniony, należy wziąć pod uwagę, które schematy uwierzytelniania zapewniają wymagany poziom zabezpieczeń. Najsłabszy standardowy schemat uwierzytelniania omówiony poniżej jest uwierzytelnianiem podstawowym. Uwierzytelnianie podstawowe nie chroni poświadczeń użytkownika. Najmocniejszy standardowy schemat uwierzytelniania to negocjowanie uwierzytelniania, w efekcie protokołu Kerberos.  
  
- Serwer nie powinien znajdować się w żadnym z schematów, które nie zostały przygotowane do zaakceptowania lub które nie zabezpieczają odpowiednio chronionego zasobu. Klienci mogą wybrać dowolny ze schematów uwierzytelniania prezentowanych przez serwer. Niektórzy klienci domyślnie mają słaby schemat uwierzytelniania lub pierwszy schemat uwierzytelniania na liście serwerów.  
  
## <a name="see-also"></a>Zobacz też

- [Przegląd zabezpieczeń transportu](transport-security-overview.md)
- [Korzystanie z personifikacji z zabezpieczeniami transportu](using-impersonation-with-transport-security.md)
- [Delegowanie i personifikacja](delegation-and-impersonation-with-wcf.md)

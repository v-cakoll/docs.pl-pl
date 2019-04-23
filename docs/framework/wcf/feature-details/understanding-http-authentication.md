---
title: Opis uwierzytelniania HTTP
ms.date: 03/30/2017
ms.assetid: 9376309a-39e3-4819-b47b-a73982b57620
ms.openlocfilehash: 430b0ddb98514b605178124f331e5152605a2b89
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/18/2019
ms.locfileid: "59206398"
---
# <a name="understanding-http-authentication"></a>Opis uwierzytelniania HTTP
Uwierzytelnianie to proces stwierdzić, czy klient jest uprawniona do dostępu do zasobu. Protokół HTTP obsługuje uwierzytelnianie jako środek negocjowania dostęp do bezpiecznych zasobów.  
  
 Początkowe żądanie od klienta jest zazwyczaj anonimowe żądania nie zawiera żadnych informacji o uwierzytelnianiu. Aplikacje serwera HTTP można odmówić anonimowego żądania podczas wskazująca, że uwierzytelnianie jest wymagane. Aplikacja serwer wysyła nagłówki WWW uwierzytelniania, aby wskazać schematów uwierzytelniania obsługiwanych. W tym dokumencie opisano kilka schematów uwierzytelniania dla protokołu HTTP i omówiono ich obsługę w Windows Communication Foundation (WCF).  
  
## <a name="http-authentication-schemes"></a>Schematy uwierzytelniania HTTP  
 Serwer można określić wielu schematów uwierzytelniania klienta do wyboru. W poniższej tabeli opisano niektóre schematów uwierzytelniania w aplikacji Windows.  
  
|Schemat uwierzytelniania|Opis|  
|---------------------------|-----------------|  
|Anonimowe|Anonimowe żądania nie zawiera żadnych informacji o uwierzytelnianiu. Jest to równoważne do udzielania wszystkim dostępu do zasobu.|  
|Podstawowy|Uwierzytelnianie podstawowe przesyła ciągu zakodowanego algorytmem Base64, który zawiera nazwę użytkownika i hasło dla klienta. Base64 nie jest formy szyfrowania i należy rozważyć takie same, jak wysyłanie nazwy użytkownika i hasła w postaci zwykłego tekstu. Jeśli zasób musi być chronione, zdecydowanie należy wziąć pod uwagę przy użyciu schematu uwierzytelniania innego niż uwierzytelnianie podstawowe.|  
|Podsumowanie|Uwierzytelnianie szyfrowane jest schemat odpowiedzi na żądanie, który ma zastąpić uwierzytelnianie podstawowe. Serwer wysyła ciąg losowych danych o nazwie *jednorazowego* do klienta jako wyzwanie. Klient odpowiada za pomocą wyznaczania wartości skrótu, który zawiera nazwę użytkownika, hasło i identyfikator jednorazowy między dodatkowe informacje. Złożoność, którą wprowadzono w tym programu exchange i mieszanie danych utrudnić kradzieży i ponownego użycia poświadczeń użytkownika przy użyciu schematu uwierzytelniania.<br /><br /> Uwierzytelnianie szyfrowane wymaga użycia konta domeny Windows. Skrót *obszaru* to nazwa domeny Windows. W związku z tym nie można użyć serwera z uruchomionym w systemie operacyjnym, który nie obsługuje domeny Windows, takie jak Windows XP Home Edition, za pomocą uwierzytelniania szyfrowanego. Z drugiej strony gdy klient działa w systemie operacyjnym, który nie obsługuje domen Windows, kontem domeny muszą być jawnie określone podczas uwierzytelniania.|  
|NTLM|Uwierzytelniania NT LAN Manager (NTLM) jest schematu odpowiedź na żądanie, który jest odmianą securer uwierzytelnianie szyfrowane. Uwierzytelnianie NTLM przy użyciu poświadczeń Windows do przekształcania danych wyzwanie, zamiast nazwy niekodowany użytkownika i hasła. Uwierzytelnianie NTLM wymaga wielu wymiany między klientem i serwerem. Na serwerze i wszystkie pośredniczące serwery proxy musi obsługiwać połączeń trwałych do pomyślnego ukończenia uwierzytelniania.|  
|Negotiate|Negocjowanie uwierzytelnienie automatycznie wybiera między protokołu Kerberos i uwierzytelnianie NTLM, w zależności od dostępności. Protokół Kerberos jest używany, jeśli jest dostępna; w przeciwnym razie zostanie podjęta próba uwierzytelniania NTLM. Uwierzytelnianie Kerberos znacznie poprawia podczas uwierzytelniania NTLM. Uwierzytelnianie Kerberos jest szybsze niż NTLM i umożliwia korzystanie z wzajemnego uwierzytelniania i delegowania poświadczeń na komputerach zdalnych.|  
|Windows Live ID|Podstawowe usługi Windows HTTP obejmuje uwierzytelnianie przy użyciu protokołów federacyjnego. Jednak standardowa transportu HTTP programu WCF nie obsługują użycia uwierzytelniania federacyjnego systemów, takich jak Microsoft Windows Live ID. Obsługa ta funkcja jest obecnie dostępne w ramach zabezpieczeń komunikatów. Aby uzyskać więcej informacji, zobacz [Federacja i wystawione tokeny](../../../../docs/framework/wcf/feature-details/federation-and-issued-tokens.md).|  
  
## <a name="choosing-an-authentication-scheme"></a>Wybieranie schematu uwierzytelniania  
 Podczas wybierania potencjalnych schematów uwierzytelniania w przypadku serwera HTTP, kilka elementów, które należy rozważyć następujące:  
  
-   Należy rozważyć, czy zasób muszą być chronione. Za pomocą uwierzytelniania HTTP wymaga przesyłania większej ilości danych i ograniczyć współdziałania z klientami. Zezwalaj na dostęp anonimowy do zasobów, które nie muszą być chronione.  
  
-   Jeśli zasób musi być chronione, należy wziąć pod uwagę schematy uwierzytelniania, które zapewniają wymaganego poziomu zabezpieczeń. Najsłabsza schemat uwierzytelniania standardowego omówionych w tym miejscu jest uwierzytelnianie podstawowe. Uwierzytelnianie podstawowe nie chroni poświadczenia użytkownika. Najsilniejszego schematu uwierzytelniania standardowego jest uwierzytelniania Negotiate, wynikiem protokołu Kerberos.  
  
-   Serwer powinien nieobecne (w nagłówkach uwierzytelniania WWW) dowolny schemat, który nie jest przygotowana do akceptowania lub które nie odpowiednio zabezpieczyć chronionego zasobu. Klienci są swobodę wyboru między dowolnymi schematy uwierzytelniania, który przedstawia informacje o serwerze. Niektórych klientów wartość domyślna to schemat słabe uwierzytelnianie lub pierwszego schematu uwierzytelniania serwera na liście.  
  
## <a name="see-also"></a>Zobacz także

- [Przegląd zabezpieczeń transportu](../../../../docs/framework/wcf/feature-details/transport-security-overview.md)
- [Korzystanie z personifikacji z zabezpieczeniami transportu](../../../../docs/framework/wcf/feature-details/using-impersonation-with-transport-security.md)
- [Delegowanie i personifikacja](../../../../docs/framework/wcf/feature-details/delegation-and-impersonation-with-wcf.md)

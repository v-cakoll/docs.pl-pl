---
title: Opis uwierzytelniania HTTP
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 9376309a-39e3-4819-b47b-a73982b57620
caps.latest.revision: "11"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 32d7df95c6acbe34a677cbd2951fd912466d015f
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="understanding-http-authentication"></a>Opis uwierzytelniania HTTP
Uwierzytelnianie to proces identyfikowania, czy klient jest uprawniona do dostępu do zasobu. Protokół HTTP obsługuje uwierzytelnianie jako negocjowania dostępu do zasobów bezpieczny sposób.  
  
 Początkowe żądanie od klienta jest zwykle anonimowe żądania nie zawiera żadnych informacji o uwierzytelnianiu. Aplikacje serwera HTTP odmówić anonimowe żądania podczas wskazująca, że uwierzytelnianie nie jest wymagane. Aplikacja wysyła nagłówków uwierzytelniania WWW, aby wskazać schematy uwierzytelniania obsługiwanych. Ten dokument opisano kilka schematy uwierzytelniania dla protokołu HTTP i omówiono ich obsługi w [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)].  
  
## <a name="http-authentication-schemes"></a>Schematy uwierzytelniania HTTP  
 Serwer można określić wielu schematów uwierzytelniania klienta do wyboru. W poniższej tabeli opisano niektóre schematów uwierzytelniania w aplikacjach systemu Windows.  
  
|Schemat uwierzytelniania|Opis|  
|---------------------------|-----------------|  
|Anonimowe|Anonimowe żądanie nie zawiera żadnych informacji o uwierzytelnianiu. Jest to równoważne wszyscy udzielanie dostępu do zasobu.|  
|Podstawowy|Uwierzytelnianie podstawowe przesyła ciąg kodowany w formacie Base64, który zawiera nazwę użytkownika i hasło dla klienta. Base64 nie jest formularzem szyfrowania i należy traktować jako taka sama, jak wysyłanie nazwy użytkownika i hasła w postaci zwykłego tekstu. Jeśli zasób musi być chronione, silnie należy rozważyć użycie schematu uwierzytelniania inne niż uwierzytelnianie podstawowe.|  
|Skrót|Uwierzytelnianie szyfrowane jest schemat odpowiedź na żądanie, który ma zastąpić uwierzytelnianie podstawowe. Serwer wysyła ciąg losowych danych o nazwie *identyfikator jednorazowy* do klienta jako żądanie. Klient wysyła wyznaczania wartości skrótu, która zawiera nazwę użytkownika, hasło i identyfikator jednorazowy między dodatkowe informacje. Złożoność, które wprowadza to z programem exchange i skrótu danych utrudnić kradzieży i ponownego użycia poświadczeń użytkownika z schematu uwierzytelniania.<br /><br /> Uwierzytelnianie szyfrowane wymaga użycia konta domeny systemu Windows. Skrót *obszaru* jest nazwą domeny systemu Windows. W związku z tym nie można użyć serwera z uruchomionym systemie operacyjnym, który nie obsługuje domen systemu Windows, takich jak system Windows XP Home Edition z uwierzytelniania szyfrowanego. Z drugiej strony gdy na komputerze klienckim działa w systemie operacyjnym, który nie obsługuje domen systemu Windows, konto domeny musi być jawnie określona podczas uwierzytelniania.|  
|UWIERZYTELNIANIE NTLM|Schemat odpowiedź na żądanie, który jest odmianą securer uwierzytelnianie szyfrowane jest uwierzytelnianie NT LAN Manager (NTLM). NTLM używa poświadczeń systemu Windows do przekształcania danych żądania zamiast nazwy niekodowany użytkownika i hasła. Uwierzytelnianie NTLM wymaga wielu wymiany między klientem a serwerem. Serwer i wszystkie pośredniczące serwery proxy musi obsługiwać połączeń trwałych do pomyślnego ukończenia uwierzytelniania.|  
|Negocjowania|Negocjowania uwierzytelniania automatycznie wybiera między protokołu Kerberos i uwierzytelniania NTLM, w zależności od dostępności. Używany jest protokół Kerberos, jeśli jest dostępna; w przeciwnym razie zostanie podjęta próba uwierzytelniania NTLM. Uwierzytelnianie Kerberos znacznie poprawia NTLM. Uwierzytelnianie Kerberos jest zarówno szybciej niż przy użyciu protokołu NTLM i umożliwia korzystanie z wzajemnego uwierzytelniania i delegowania poświadczeń do komputerów zdalnych.|  
|Windows Live ID|Podstawowe usługi HTTP systemu Windows zawiera uwierzytelniania przy użyciu protokołów federacyjnych. Jednak transporty standardowego protokołu HTTP w [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] nie obsługują użycia uwierzytelniania federacyjnego systemów, takich jak Microsoft Windows Live ID. Obsługa ta funkcja jest obecnie dostępne w ramach zabezpieczeń komunikatów. [!INCLUDE[crdefault](../../../../includes/crdefault-md.md)][Federacja i wystawione tokeny](../../../../docs/framework/wcf/feature-details/federation-and-issued-tokens.md).|  
  
## <a name="choosing-an-authentication-scheme"></a>Wybieranie schematu uwierzytelniania  
 Podczas wybierania potencjalnych schematy uwierzytelniania dla serwera HTTP, należy wziąć pod uwagę kilka elementów są następujące:  
  
-   Należy rozważyć, czy zasób powinien być chronione. Za pomocą uwierzytelniania HTTP wymaga przesyłania danych i ograniczyć współdziałania z klientami. Zezwalaj na dostęp anonimowy do zasobów, które nie są chronione.  
  
-   Jeśli zasób musi być chronione, należy wziąć pod uwagę schematy uwierzytelniania, które zapewniają wymaganego poziomu zabezpieczeń. Najsłabszą schemat uwierzytelniania standardowego omówione w tym miejscu jest uwierzytelnianie podstawowe. Uwierzytelnianie podstawowe nie chroni poświadczenia użytkownika. Najsilniejszego schematu standardowe uwierzytelnianie jest Negotiate uwierzytelniania, co powoduje protokołu Kerberos.  
  
-   Serwer powinien nieobecne (w nagłówkach WWW uwierzytelniania) żadnego schematu, która nie jest przygotowany do akceptowania lub że nie można ją było właściwie zabezpieczyć chronionego zasobu. Klienci mogą wybranie wszystkich systemów uwierzytelniania, który przedstawia informacje o serwerze. Niektóre domyślne klientów schemat uwierzytelniania słabych lub pierwszy schemat uwierzytelniania serwera na liście.  
  
## <a name="see-also"></a>Zobacz też  
 [Przegląd zabezpieczeń transportu](../../../../docs/framework/wcf/feature-details/transport-security-overview.md)  
 [Korzystanie z personifikacji z zabezpieczeniami transportu](../../../../docs/framework/wcf/feature-details/using-impersonation-with-transport-security.md)  
 [Delegowanie i personifikacja](../../../../docs/framework/wcf/feature-details/delegation-and-impersonation-with-wcf.md)

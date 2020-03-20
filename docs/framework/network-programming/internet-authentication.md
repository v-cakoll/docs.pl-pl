---
title: Uwierzytelnianie internetowe
ms.date: 03/30/2017
helpviewer_keywords:
- authentication [.NET Framework], classes
- IAuthenticationModule interface
- ICredentialLookup interface
- CredentialCache class, about CredentialCache class
- receiving data, authentication
- AuthenticationManager class, about AuthenticationManager class
- Internet, authentication
- sending data, authentication
- network resources, authentication
- user authentication, classes for authentication
- NetworkCredential class, about NetworkCredential class
- client authentication, classes for authentication
ms.assetid: d342e87c-f672-4660-a513-41a2f2b80c4a
ms.openlocfilehash: 3e0b5cd58270cec758db5d4dad6f3ad48962921a
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/15/2020
ms.locfileid: "71047919"
---
# <a name="internet-authentication"></a>Uwierzytelnianie internetowe
Klasy <xref:System.Net> obsługują różne mechanizmy uwierzytelniania klienta, w tym standardowe metody uwierzytelniania internetowego podstawowe, szyfrowane, negocjują, NTLM i uwierzytelnianie Kerberos, a także metody niestandardowe, które można utworzyć.  
  
 Poświadczenia uwierzytelniania są <xref:System.Net.NetworkCredential> przechowywane <xref:System.Net.CredentialCache> w klasach <xref:System.Net.ICredentials> i, które implementują interfejs. Gdy jedna z tych klas jest wyszukiwana pod kątem poświadczeń, zwraca **wystąpienie networkcredential** klasy. Proces uwierzytelniania jest <xref:System.Net.AuthenticationManager> zarządzany przez klasę, a rzeczywisty proces uwierzytelniania jest <xref:System.Net.IAuthenticationModule> wykonywany przez klasę modułu uwierzytelniania, która implementuje interfejs. Musisz zarejestrować niestandardowy moduł uwierzytelniania za pomocą **AuthenticationManager,** zanim będzie można go używać; moduły dla metod uwierzytelniania podstawowego, digest, negotiate, NTLM i Kerberos są domyślnie rejestrowane.  
  
 **NetworkCredential** przechowuje zestaw poświadczeń skojarzonych z jednym zasobem internetowym identyfikowanym przez <xref:System.Net.NetworkCredential.GetCredential%2A> identyfikator URI i zwraca je w odpowiedzi na każde wywołanie metody. **NetworkCredential** Klasa jest zwykle używany przez aplikacje, które uzyskują dostęp do ograniczonej liczby zasobów internetowych lub przez aplikacje, które używają tego samego zestawu poświadczeń we wszystkich przypadkach.  
  
 **Klasa CredentialCache przechowuje** kolekcję poświadczeń dla różnych zasobów sieci Web. Gdy <xref:System.Net.CredentialCache.GetCredential%2A> metoda jest wywoływana, **CredentialCache** zwraca odpowiedni zestaw poświadczeń, zgodnie z ustaleniami identyfikatora URI zasobu sieci Web i żądanego schematu uwierzytelniania. Aplikacje korzystające z różnych zasobów internetowych z różnymi schematami uwierzytelniania korzystają z **używania credentialcache** klasy, ponieważ przechowuje wszystkie poświadczenia i udostępnia je zgodnie z żądaniem.  
  
 Gdy zasób internetowy <xref:System.Net.WebRequest.GetResponse%2A?displayProperty=nameWithType> żąda uwierzytelniania, metoda wysyła <xref:System.Net.WebRequest> do Menedżera **uwierzytelniania** wraz z żądaniem poświadczeń. Żądanie jest następnie uwierzytelniane zgodnie z następującym procesem:  
  
1. **AuthenticationManager** wywołuje <xref:System.Net.IAuthenticationModule.Authenticate%2A> metodę na każdym z zarejestrowanych modułów uwierzytelniania w kolejności, w jakiej zostały zarejestrowane. **AuthenticationManager** używa pierwszego modułu, który nie zwraca **wartości null** do przeprowadzenia procesu uwierzytelniania. Szczegóły procesu różnią się w zależności od typu modułu uwierzytelniania.  
  
2. Po zakończeniu procesu uwierzytelniania moduł uwierzytelniania zwraca <xref:System.Net.Authorization> do **WebRequest,** który zawiera informacje potrzebne do uzyskania dostępu do zasobu internetowego.  
  
 Niektóre schematy uwierzytelniania mogą uwierzytelniać użytkownika bez uprzedniego żądania zasobu. Aplikacja może zaoszczędzić czas, preauthenticating użytkownika z zasobem, eliminując w ten sposób co najmniej jedną podróż w obie strony do serwera. Lub może wykonać uwierzytelnianie podczas uruchamiania programu, aby być bardziej elastyczne dla użytkownika później. Schematy uwierzytelniania, które mogą używać preauthentication ustawić <xref:System.Net.IAuthenticationModule.PreAuthenticate%2A> właściwość true . **true**  
  
## <a name="see-also"></a>Zobacz też

- [Uwierzytelnianie podstawowe i szyfrowane](basic-and-digest-authentication.md)
- [Uwierzytelnianie NTLM i uwierzytelnianie Kerberos](ntlm-and-kerberos-authentication.md)
- [Zabezpieczenia w programowaniu sieciowym](security-in-network-programming.md)

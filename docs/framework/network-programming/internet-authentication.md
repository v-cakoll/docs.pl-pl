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
author: mcleblanc
ms.author: markl
ms.openlocfilehash: e0f1ad373f8ec7687b44856a53e1e35b8b6baf8c
ms.sourcegitcommit: 213292dfbb0c37d83f62709959ff55c50af5560d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/25/2018
ms.locfileid: "47089065"
---
# <a name="internet-authentication"></a>Uwierzytelnianie internetowe
<xref:System.Net> Klasy obsługi różnych mechanizmów uwierzytelniania klienta, w tym standardowa Internet metod uwierzytelniania, podstawowe, szyfrowane, negocjowania NTLM, a uwierzytelnianie Kerberos, a także niestandardowych metod, które można utworzyć.  
  
 Poświadczenia uwierzytelniania są przechowywane w <xref:System.Net.NetworkCredential> i <xref:System.Net.CredentialCache> klas, które implementują <xref:System.Net.ICredentials> interfejsu. Gdy jeden z tych klas zostanie zapytany o poświadczenia, zwraca wystąpienie **NetworkCredential** klasy. Proces uwierzytelniania jest zarządzana przez <xref:System.Net.AuthenticationManager> klasy, a proces uwierzytelniania rzeczywiste odbywa się przez klasę moduł uwierzytelniania, która implementuje <xref:System.Net.IAuthenticationModule> interfejsu. Musisz się zarejestrować, moduł uwierzytelniania niestandardowego o **słowniku** zanim będzie można używać; moduły podstawowe, szyfrowane negocjowania NTLM, i metody uwierzytelniania Kerberos jest zarejestrowana domyślnie.  
  
 **NetworkCredential** przechowuje zestaw poświadczeń skojarzonych z pojedynczego zasobu internetowego identyfikowane przez identyfikator URI i zwraca je w odpowiedzi na każde wywołanie <xref:System.Net.NetworkCredential.GetCredential%2A> metody. **NetworkCredential** klasa jest zazwyczaj używana przez aplikacje uzyskujące dostęp do ograniczonej liczby zasoby internetowe lub aplikacje, które używają tego samego zestawu poświadczeń we wszystkich przypadkach.  
  
 **CredentialCache** klasa przechowuje kolekcję poświadczeń dla różnych zasobów sieci Web. Gdy <xref:System.Net.CredentialCache.GetCredential%2A> metoda jest wywoływana, **CredentialCache** zwraca odpowiedniego zestawu poświadczeń, zgodnie z ustaleniami identyfikator URI zasobu sieci Web i schemat uwierzytelniania żądanej. Aplikacje, które używają różnych zasobów w Internecie przy użyciu schematów uwierzytelniania różnych korzyści ze stosowania **CredentialCache** klasy, ponieważ przechowuje wszystkie poświadczenia i udostępnia je zgodnie z żądaniem.  
  
 Podczas uwierzytelniania, żądania zasobów internetowych <xref:System.Net.WebRequest.GetResponse%2A?displayProperty=nameWithType> metoda wysyła <xref:System.Net.WebRequest> do **słowniku** wraz z żądaniem o poświadczenia. Żądanie jest uwierzytelniane zgodnie z następującego procesu:  
  
1.  **Słowniku** wywołania <xref:System.Net.IAuthenticationModule.Authenticate%2A> metoda dla każdego z modułów uwierzytelniania zarejestrowanego w kolejności, zostały one zarejestrowane. **Słowniku** używa pierwszego modułu, która nie zwraca **null** przeprowadzić proces uwierzytelniania. Szczegółowe informacje o procesie różnią się w zależności od typu uwierzytelniania modułu związane.  
  
2.  Po zakończeniu procesu uwierzytelniania moduł uwierzytelniania zwraca <xref:System.Net.Authorization> do **WebRequest** zawierający informacje wymagane do dostępu do zasobu internetowego.  
  
 Niektóre schematy uwierzytelniania można uwierzytelnić użytkownika bez wcześniejszego utworzenia żądania dla zasobu. Aplikację można zaoszczędzić czas i preauthenticating użytkownika z zasobem, eliminując co najmniej jedną rundę do serwera. Lub, aby później można zwiększyć szybkość reakcji użytkownika może wykonywać uwierzytelnianie podczas uruchamiania programu. Schematy uwierzytelniania, które można użyć uwierzytelniania wstępnego zestawu <xref:System.Net.IAuthenticationModule.PreAuthenticate%2A> właściwości **true**.  
  
## <a name="see-also"></a>Zobacz też  
 [Uwierzytelnianie podstawowe i szyfrowane](../../../docs/framework/network-programming/basic-and-digest-authentication.md)  
 [Uwierzytelnianie NTLM i uwierzytelnianie Kerberos](../../../docs/framework/network-programming/ntlm-and-kerberos-authentication.md)  
 [Zabezpieczenia w programowaniu sieciowym](../../../docs/framework/network-programming/security-in-network-programming.md)

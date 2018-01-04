---
title: Uwierzytelnianie Internet
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
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
caps.latest.revision: "11"
author: mcleblanc
ms.author: markl
manager: markl
ms.workload: dotnet
ms.openlocfilehash: fbf25ae866b338d2f1ac0ea11570e0d535e9137c
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="internet-authentication"></a>Uwierzytelnianie Internet
<xref:System.Net> Klasy obsługi różnych mechanizmów uwierzytelniania klienta, w tym standardowe Internet metod uwierzytelniania, podstawowe, szyfrowane, negocjowania, NTLM, a uwierzytelnianie Kerberos, a także metod niestandardowych, które można utworzyć.  
  
 Poświadczenia uwierzytelniania są przechowywane w <xref:System.Net.NetworkCredential> i <xref:System.Net.CredentialCache> klas implementujących <xref:System.Net.ICredentials> interfejsu. Gdy jedna z tych klas zostanie zapytany o poświadczenia, zwraca wystąpienie **NetworkCredential** klasy. Proces uwierzytelniania jest zarządzana przez <xref:System.Net.AuthenticationManager> klasy, a proces uwierzytelniania rzeczywiste odbywa się za pośrednictwem klasy modułu uwierzytelniania, która implementuje <xref:System.Net.IAuthenticationModule> interfejsu. Zarejestruj moduł uwierzytelniania niestandardowego o **AuthenticationManager** przed jej użyciem; negocjowania modułów podstawowe, szyfrowane, NTLM, i metod uwierzytelniania Kerberos jest zarejestrowana domyślnie.  
  
 **NetworkCredential** przechowuje zestaw poświadczeń skojarzonych z pojedynczego zasobu internetowego identyfikowany przez identyfikator URI i zwraca je w odpowiedzi na każde wywołanie <xref:System.Net.NetworkCredential.GetCredential%2A> metody. **NetworkCredential** klasy jest zwykle używany przez aplikacje, które uzyskują dostęp do ograniczonej liczby zasobów w Internecie lub aplikacji, które używają tego samego zestawu poświadczeń we wszystkich przypadkach.  
  
 **CredentialCache** klasy przechowuje zbierania poświadczeń dla różnych zasobów sieci Web. Gdy <xref:System.Net.CredentialCache.GetCredential%2A> metoda jest wywoływana, **CredentialCache** zwraca prawidłowego zestawu poświadczeń, zgodnie z ustaleniami zasobu sieci Web i schemat uwierzytelniania żądanego identyfikatora URI. Aplikacje, które korzystają z różnych zasobów internetowych z systemami uwierzytelniania inny korzyści ze stosowania **CredentialCache** klasy, ponieważ przechowuje wszystkie poświadczenia i udostępnia je zgodnie z żądaniem.  
  
 Podczas uwierzytelniania żądania zasobów internetowych <xref:System.Net.WebRequest.GetResponse%2A?displayProperty=nameWithType> wysyła metody <xref:System.Net.WebRequest> do **AuthenticationManager** wraz z żądaniem poświadczeń. Żądanie jest uwierzytelniane zgodnie z następujący proces:  
  
1.  **AuthenticationManager** wywołania <xref:System.Net.IAuthenticationModule.Authenticate%2A> metody na każdym z modułami uwierzytelniania zarejestrowanych w kolejności, zostały one zarejestrowane. **AuthenticationManager** używa pierwszego modułu, która nie zwraca **null** przeprowadzenie procesu uwierzytelniania. Szczegóły procesu różnią się zależnie od typu zaangażowany moduł uwierzytelniania.  
  
2.  Po zakończeniu procesu uwierzytelniania moduł uwierzytelniania zwraca <xref:System.Net.Authorization> do **WebRequest** zawierający informacje potrzebne do dostępu do zasobu internetowego.  
  
 Niektóre schematy uwierzytelniania można uwierzytelnić użytkownika bez wcześniejszego utworzenia żądania dla zasobu. Aplikacja może zaoszczędzić czas preauthenticating użytkownika z zasobem, eliminując co najmniej jeden obiegu do serwera. Lub może przeprowadzać uwierzytelnianie podczas uruchamiania programu Aby później można bardziej odpowiednie dla użytkownika. Schematy uwierzytelniania, korzystających z uwierzytelniania wstępnego zestawu <xref:System.Net.IAuthenticationModule.PreAuthenticate%2A> właściwości **true**.  
  
## <a name="see-also"></a>Zobacz też  
 [Uwierzytelnianie podstawowe i szyfrowane](../../../docs/framework/network-programming/basic-and-digest-authentication.md)  
 [Uwierzytelnianie NTLM i uwierzytelnianie Kerberos](../../../docs/framework/network-programming/ntlm-and-kerberos-authentication.md)  
 [Zabezpieczenia w programowaniu sieciowym](../../../docs/framework/network-programming/security-in-network-programming.md)

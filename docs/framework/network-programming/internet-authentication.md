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
ms.sourcegitcommit: 289e06e904b72f34ac717dbcc5074239b977e707
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/17/2019
ms.locfileid: "71047919"
---
# <a name="internet-authentication"></a>Uwierzytelnianie internetowe
<xref:System.Net> Klasy obsługują różne mechanizmy uwierzytelniania klientów, w tym standardowe metody uwierzytelniania internetowego Basic, Digest, Negotiate, NTLM i Kerberos, a także metody niestandardowe, które można utworzyć.  
  
 Poświadczenia uwierzytelniania są przechowywane w <xref:System.Net.NetworkCredential> <xref:System.Net.ICredentials> klasach <xref:System.Net.CredentialCache> i, które implementują interfejs. Gdy jedna z tych klas jest kwerendą dla poświadczeń, zwraca wystąpienie klasy **NetworkCredential** . Proces uwierzytelniania jest zarządzany przez <xref:System.Net.AuthenticationManager> klasę, a rzeczywisty proces uwierzytelniania jest wykonywany przez klasę modułu uwierzytelniania, która <xref:System.Net.IAuthenticationModule> implementuje interfejs. Aby można było użyć niestandardowego **modułu uwierzytelniania,** należy zarejestrować go. moduły dla metod uwierzytelniania podstawowa, Digest, Negotiate, NTLM i Kerberos są domyślnie zarejestrowane.  
  
 **NetworkCredential** przechowuje zestaw poświadczeń skojarzonych z pojedynczym zasobem internetowym identyfikowanym przez identyfikator URI i zwraca je w odpowiedzi na każde wywołanie <xref:System.Net.NetworkCredential.GetCredential%2A> metody. Klasa **NetworkCredential** jest zwykle używana przez aplikacje, które uzyskują dostęp do ograniczonej liczby zasobów internetowych lub przez aplikacje korzystające z tego samego zestawu poświadczeń we wszystkich przypadkach.  
  
 Klasa **CredentialCache** przechowuje kolekcję poświadczeń dla różnych zasobów sieci Web. Gdy metoda jest wywoływana, CredentialCache zwraca właściwy zestaw poświadczeń, określony przez identyfikator URI zasobu sieci Web i żądany schemat uwierzytelniania. <xref:System.Net.CredentialCache.GetCredential%2A> Aplikacje korzystające z różnych zasobów internetowych z różnymi schematami uwierzytelniania korzystają z klasy **CredentialCache** , ponieważ przechowuje wszystkie poświadczenia i udostępnia je zgodnie z żądaniem.  
  
 Gdy zasób internetowy żąda uwierzytelnienia, <xref:System.Net.WebRequest.GetResponse%2A?displayProperty=nameWithType> Metoda <xref:System.Net.WebRequest> wysyła do elementu **AuthenticationManager** wraz z żądaniem poświadczeń. Żądanie jest następnie uwierzytelniane zgodnie z następującym procesem:  
  
1. <xref:System.Net.IAuthenticationModule.Authenticate%2A> Metoda **AuthenticationManager** wywołuje metodę dla każdego z zarejestrowanych modułów uwierzytelniania w kolejności, w której zostały zarejestrowane. Program **AuthenticationManager** używa pierwszego modułu, który nie zwraca **wartości null** w celu przeprowadzenia procesu uwierzytelniania. Szczegóły procesu różnią się w zależności od typu używanego modułu uwierzytelniania.  
  
2. Po zakończeniu procesu uwierzytelniania moduł uwierzytelniania zwraca <xref:System.Net.Authorization> do **żądania webżądanie** , które zawiera informacje konieczne do uzyskania dostępu do zasobu internetowego.  
  
 Niektóre schematy uwierzytelniania mogą uwierzytelniać użytkownika bez uprzedniego utworzenia żądania dla zasobu. Aplikacja może zaoszczędzić czas poprzez preuwierzytelnianie użytkownika przy użyciu zasobu, co eliminuje co najmniej jedną rundę na serwerze. Można też przeprowadzić uwierzytelnianie podczas uruchamiania programu w celu późniejszego reagowania na użytkownika. Schematy uwierzytelniania, które mogą używać wstępnego uwierzytelniania <xref:System.Net.IAuthenticationModule.PreAuthenticate%2A> , mają ustawioną właściwość na **wartość true**.  
  
## <a name="see-also"></a>Zobacz także

- [Uwierzytelnianie podstawowe i szyfrowane](basic-and-digest-authentication.md)
- [Uwierzytelnianie NTLM i uwierzytelnianie Kerberos](ntlm-and-kerberos-authentication.md)
- [Zabezpieczenia w programowaniu sieciowym](security-in-network-programming.md)

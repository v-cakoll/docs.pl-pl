---
title: Uruchamianie aplikacji intranetowych w trybie pełnego zaufania
ms.date: 03/30/2017
helpviewer_keywords:
- full trust, running intranet applications in
- intranet applications, running in full trust
- running intranet applications in full trust
ms.assetid: ee13c0a8-ab02-49f7-b8fb-9eab16c6c4f0
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 3c6f58ef5bd96d8a74ce27bb53acd36af005c335
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="running-intranet-applications-in-full-trust"></a>Uruchamianie aplikacji intranetowych w trybie pełnego zaufania
W programie .NET Framework w wersji 3.5 Service Pack 1 (SP1), aplikacji i ich zestawy bibliotek mogą być uruchamiane jako zestawy pełnego zaufania z udziału sieciowego. <xref:System.Security.SecurityZone.MyComputer> dowód strefy jest automatycznie dodawany do zestawów, które są ładowane z udziału w sieci intranet. To świadectwo zapewnia te zestawy, takie same udzielić zestaw (co jest zazwyczaj pełnego zaufania) jako zestawy, które znajdują się na komputerze. Ta funkcja nie ma zastosowania do aplikacji ClickOnce lub aplikacje, które są zaprojektowane do uruchamiania na hoście.  
  
## <a name="rules-for-library-assemblies"></a>Zasady zestawy bibliotek  
 Zestawy, które zostały załadowane przez plik wykonywalny w udziale sieciowym mają zastosowanie następujące reguły:  
  
-   Zestawy bibliotek musi znajdować się w tym samym folderze co zestawu pliku wykonywalnego. Zestawy, które znajdują się w podfolderze lub odwołuje się z inną ścieżką nie podano zestaw uprawnień pełnego zaufania.  
  
-   Jeśli plik wykonywalny opóźnienie do pobrania zestawu, należy użyć tej samej ścieżki, które zostało użyte do uruchomienia pliku wykonywalnego. Na przykład jeśli udział \\ \\ *komputera sieciowego*\\*udostępnianie* jest zamapowane na literę dysku i plik wykonywalny uruchamiany z tej ścieżki, zestawy, które są ładowane przez plik wykonywalny przy użyciu ścieżki sieciowej zostanie nie można przyznać pełne zaufanie. Aby załadować z opóźnieniem zestawu w <xref:System.Security.SecurityZone.MyComputer> strefy, plik wykonywalny, należy użyć ścieżki litery dysku.  
  
## <a name="restoring-the-former-intranet-policy"></a>Przywracanie zasad wcześniejsze sieci Intranet  
 We wcześniejszych wersjach programu .NET Framework, zestawy udostępnione zostały przyznane <xref:System.Security.SecurityZone.Intranet> dowód strefy. Konieczne było określić zasady zabezpieczeń dostępu kodu, aby przyznać pełne zaufanie do zestawu w udziale.  
  
 To nowe zachowanie jest ustawieniem domyślnym dla zestawów sieci intranet. Możesz wrócić do wcześniejszych zachowanie udostępniania <xref:System.Security.SecurityZone.Intranet> dowód, ustawiając klucz rejestru, która ma zastosowanie do wszystkich aplikacji na komputerze. Ten proces jest inny dla komputerów 32-bitowe i 64-bitowe:  
  
-   Na komputerach z 32-bitowy, utwórz podklucz w obszarze HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\\. NETFramework klucz w rejestrze systemu. Nazwa klucza LegacyMyComputerZone za pomocą wartość DWORD na 1.  
  
-   Na komputerach 64-bitowych, utwórz podklucz w obszarze HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\\. NETFramework klucz w rejestrze systemu. Nazwa klucza LegacyMyComputerZone za pomocą wartość DWORD na 1. Utwórz podklucz tym samym obszarze HKEY_LOCAL_MACHINE\SOFTWARE\Wow6432Node\Microsoft\\. Klucz NETFramework.  
  
## <a name="see-also"></a>Zobacz też  
 [Programowanie za pomocą zestawów](../../../docs/framework/app-domains/programming-with-assemblies.md)

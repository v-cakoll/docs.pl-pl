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
ms.openlocfilehash: e8731e90a66c20f06e8afcd7458349cbc0b93484
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/08/2019
ms.locfileid: "59084107"
---
# <a name="running-intranet-applications-in-full-trust"></a>Uruchamianie aplikacji intranetowych w trybie pełnego zaufania
Począwszy od .NET Framework w wersji 3.5 z dodatkiem Service Pack 1 (SP1), aplikacje i ich zestawy biblioteki może działać jako zestawów pełnego zaufania z udziału sieciowego. <xref:System.Security.SecurityZone.MyComputer> dowód strefy jest automatycznie dodawany do zestawów, które są ładowane z udziału w sieci intranet. Dowód ten zapewnia te zestawy, takie same udzielić zestaw (co jest zazwyczaj pełne zaufanie) jako zestawy, które znajdują się na komputerze. Ta funkcja nie ma zastosowania do aplikacji ClickOnce lub aplikacje, które są przeznaczone do uruchamiania na hoście.  
  
## <a name="rules-for-library-assemblies"></a>Zasady zestawy bibliotek  
 Obowiązują następujące reguły do zestawów, które są ładowane przez plik wykonywalny w udziale sieciowym:  
  
-   Zestawy bibliotek musi znajdować się w tym samym folderze co zestawu pliku wykonywalnego. Zestawy, które znajdują się w podfolderze lub do których istnieją odwołania z inną ścieżką nie zawierają zestaw uprawnień pełnego zaufania.  
  
-   Jeśli plik wykonywalny opóźnienie do pobrania zestawu, musi on używać tej samej ścieżki, który został użyty do uruchomienia pliku wykonywalnego. Na przykład jeśli udział \\ \\ *komputera sieciowego*\\*udostępnianie* jest mapowany na literę dysku i pliku wykonywalnego, który jest uruchamiany z tej ścieżki zestawów, które są ładowane przez plik wykonywalny przy użyciu ścieżki sieciowej nie uzyska pełnego zaufania. Aby załadować z opóźnieniem elementu zestawu w <xref:System.Security.SecurityZone.MyComputer> strefy, plik wykonywalny, należy użyć ścieżki literę dysku.  
  
## <a name="restoring-the-former-intranet-policy"></a>Przywracanie zasady były sieci Intranet  
 We wcześniejszych wersjach programu .NET Framework, zestawów współużytkowanych zostały przyznane <xref:System.Security.SecurityZone.Intranet> strefa dowodów. Trzeba było określić zasady zabezpieczeń dostępu kodu, aby przyznać pełne zaufanie do zestawu w udziale.  
  
 To nowe zachowanie jest ustawieniem domyślnym dla zestawów w sieci intranet. Możesz wrócić do wcześniejszej zachowanie związanych z udostępnianiem <xref:System.Security.SecurityZone.Intranet> dowód, ustawiając klucz rejestru, który ma zastosowanie do wszystkich aplikacji na komputerze. Ten proces różni się dla komputerów 32-bitowych i 64-bitowych:  
  
-   Na komputerach z 32-bitowych, utwórz podklucz w obszarze HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\\. NETFramework klucz w rejestrze systemowym. Nazwa klucza LegacyMyComputerZone za pomocą wartość DWORD na 1.  
  
-   Na komputerach 64-bitowych, utwórz podklucz w obszarze HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\\. NETFramework klucz w rejestrze systemowym. Nazwa klucza LegacyMyComputerZone za pomocą wartość DWORD na 1. Utwórz ten sam go w obszarze HKEY_LOCAL_MACHINE\SOFTWARE\Wow6432Node\Microsoft\\. Klucz NETFramework.  
  
## <a name="see-also"></a>Zobacz także

- [Programowanie za pomocą zestawów](../../../docs/framework/app-domains/programming-with-assemblies.md)

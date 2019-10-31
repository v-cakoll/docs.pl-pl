---
title: Uruchamianie aplikacji intranetowych w trybie pełnego zaufania
ms.date: 03/30/2017
helpviewer_keywords:
- full trust, running intranet applications in
- intranet applications, running in full trust
- running intranet applications in full trust
ms.assetid: ee13c0a8-ab02-49f7-b8fb-9eab16c6c4f0
ms.openlocfilehash: c93f84dc53abbb86cbfc4ae36e9cdcbe0bd50273
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/30/2019
ms.locfileid: "73119756"
---
# <a name="running-intranet-applications-in-full-trust"></a>Uruchamianie aplikacji intranetowych w trybie pełnego zaufania

Począwszy od .NET Framework w wersji 3,5 Service Pack 1 (SP1), aplikacje i ich zestawy bibliotek można uruchamiać jako zestawy pełnego zaufania z udziału sieciowego. <xref:System.Security.SecurityZone.MyComputer>e dowody strefy są automatycznie dodawane do zestawów, które są ładowane z udziału w intranecie. Ten dowód przyznaje tym zestawom ten sam zbiór (który jest zazwyczaj pełnym zaufaniem) jako zestawy, które znajdują się na komputerze. Ta funkcja nie dotyczy aplikacji ClickOnce ani aplikacji, które są przeznaczone do uruchamiania na hoście.  
  
## <a name="rules-for-library-assemblies"></a>Reguły dla zestawów bibliotek  

Następujące reguły mają zastosowanie do zestawów, które są ładowane przez plik wykonywalny w udziale sieciowym:  
  
- Zestawy bibliotek muszą znajdować się w tym samym folderze co zestaw wykonywalny. Zestawy, które znajdują się w podfolderze lub odwołują się do innej ścieżki, nie mają ustawionego pełnego zaufania.  
  
- Jeśli plik wykonywalny opóźni-ładuje zestaw, musi używać tej samej ścieżki, która została użyta do uruchomienia pliku wykonywalnego. Na przykład, jeśli udział \\\\*Network-computer*\\*Share* jest mapowany na literę dysku, a plik wykonywalny jest uruchamiany z tej ścieżki, zestawy, które są ładowane przez plik wykonywalny przy użyciu ścieżki sieciowej, nie zostaną przyznane pełne ufał. Aby opóźnić ładowanie zestawu w strefie <xref:System.Security.SecurityZone.MyComputer>, plik wykonywalny musi używać ścieżki litery dysku.  
  
## <a name="restoring-the-former-intranet-policy"></a>Przywracanie wcześniejszych zasad intranetu  

We wcześniejszych wersjach .NET Framework przydzielono zestawy udostępnione <xref:System.Security.SecurityZone.Intranet>ą dowody strefy. Należy określić zasady zabezpieczeń dostępu kodu w celu przyznania pełnego zaufania do zestawu w udziale.  
  
To nowe zachowanie jest domyślne dla zestawów intranetowych. Możesz powrócić do wcześniejszego zachowania <xref:System.Security.SecurityZone.Intranet> dowód, ustawiając klucz rejestru dotyczący wszystkich aplikacji na komputerze. Ten proces jest różny dla komputerów 32-bitowych i 64-bitowych:  
  
- Na komputerach 32-bitowych Utwórz podklucz w\\HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft. Klucz NETFramework w rejestrze systemowym. Użyj nazwy klucza LegacyMyComputerZone z wartością DWORD równą 1.  
  
- Na komputerach 64-bitowych Utwórz podklucz w\\HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft. Klucz NETFramework w rejestrze systemowym. Użyj nazwy klucza LegacyMyComputerZone z wartością DWORD równą 1. Utwórz ten sam podklucz w\\HKEY_LOCAL_MACHINE\SOFTWARE\Wow6432Node\Microsoft. Klucz NETFramework.  
  
## <a name="see-also"></a>Zobacz także

- [Programowanie za pomocą zestawów](../../standard/assembly/program.md)

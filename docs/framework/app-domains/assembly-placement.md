---
title: Umieszczanie zestawu
ms.date: 03/30/2017
helpviewer_keywords:
- <codeBase> element
- locating assemblies
- assemblies [.NET Framework], placement
- assemblies [.NET Framework], location
ms.assetid: ff8d48bc-f606-484f-9fe1-d0af264269fb
ms.openlocfilehash: 5eb7b5c35bb40d5a58390ccbd4619cbed4e06c52
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/30/2019
ms.locfileid: "73119958"
---
# <a name="assembly-placement"></a>Umieszczanie zestawu
W przypadku większości aplikacji .NET Framework można zlokalizować zestawy, które tworzą aplikację w katalogu aplikacji, w podkatalogu katalogu aplikacji lub w globalnej pamięci podręcznej zestawów (Jeśli zestaw jest udostępniony). Można przesłonić, gdzie środowisko uruchomieniowe języka wspólnego szuka zestawu przy użyciu [ \<kodu bazowej>](../configure-apps/file-schema/runtime/codebase-element.md) w pliku konfiguracyjnym. Jeśli zestaw nie ma silnej nazwy, lokalizacja określona przy użyciu [ \<bazowej kodu> element](../configure-apps/file-schema/runtime/codebase-element.md) jest ograniczone do katalogu aplikacji lub podkatalogu. Jeśli zestaw ma silną nazwę, [ \<baza kodu> element](../configure-apps/file-schema/runtime/codebase-element.md) może określić dowolną lokalizację na komputerze lub w sieci.  
  
 Podobne reguły dotyczą lokalizowania zestawów podczas pracy z niezarządzanym kodem lub aplikacjami międzyoperacyjnymi modelu COM: Jeśli zestaw będzie współużytkowany przez wiele aplikacji, powinien być zainstalowany w globalnej pamięci podręcznej zestawów. Zestawy używane z kodem niezarządzanym muszą zostać wyeksportowane jako biblioteka typów i zarejestrowane. Zestawy używane przez międzyoperacyjność modelu COM muszą być zarejestrowane w wykazie, chociaż w niektórych przypadkach ta rejestracja odbywa się automatycznie.  
  
## <a name="see-also"></a>Zobacz też

- [Sposoby lokalizowania zestawów przez środowisko uruchomieniowe](../deployment/how-the-runtime-locates-assemblies.md)
- [Konfigurowanie aplikacji](../configure-apps/index.md)
- [Współdziałanie z kodem niezarządzanym](../interop/index.md)
- [Zestawy w środowisku .NET](index.md)

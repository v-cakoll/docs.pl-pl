---
title: Umieszczanie zestawu
description: Przejrzyj wskazówki dotyczące umieszczania zestawów .NET w katalogach (na przykład w globalnej pamięci podręcznej zestawów lub w katalogu lub podkatalogu aplikacji).
ms.date: 03/30/2017
helpviewer_keywords:
- <codeBase> element
- locating assemblies
- assemblies [.NET Framework], placement
- assemblies [.NET Framework], location
ms.assetid: ff8d48bc-f606-484f-9fe1-d0af264269fb
ms.openlocfilehash: 3106f6f01229057725cbc2e8e689a4e2247f95e6
ms.sourcegitcommit: 1c37a894c923bea021a3cc38ce7cba946357bbe1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/19/2020
ms.locfileid: "85104956"
---
# <a name="assembly-placement"></a>Umieszczanie zestawu
W przypadku większości aplikacji .NET Framework można zlokalizować zestawy, które tworzą aplikację w katalogu aplikacji, w podkatalogu katalogu aplikacji lub w globalnej pamięci podręcznej zestawów (Jeśli zestaw jest udostępniony). Można przesłonić, gdzie środowisko uruchomieniowe języka wspólnego szuka zestawu przy użyciu [ \<codeBase> elementu](../configure-apps/file-schema/runtime/codebase-element.md) w pliku konfiguracji. Jeśli zestaw nie ma silnej nazwy, lokalizacja określona za pomocą [ \<codeBase> elementu](../configure-apps/file-schema/runtime/codebase-element.md) jest ograniczona do katalogu aplikacji lub podkatalogu. Jeśli zestaw ma silną nazwę, [ \<codeBase> element](../configure-apps/file-schema/runtime/codebase-element.md) może określić dowolną lokalizację na komputerze lub w sieci.  
  
 Podobne reguły dotyczą lokalizowania zestawów podczas pracy z niezarządzanym kodem lub aplikacjami międzyoperacyjnymi modelu COM: Jeśli zestaw będzie współużytkowany przez wiele aplikacji, powinien być zainstalowany w globalnej pamięci podręcznej zestawów. Zestawy używane z kodem niezarządzanym muszą zostać wyeksportowane jako biblioteka typów i zarejestrowane. Zestawy używane przez międzyoperacyjność modelu COM muszą być zarejestrowane w wykazie, chociaż w niektórych przypadkach ta rejestracja odbywa się automatycznie.  
  
## <a name="see-also"></a>Zobacz też

- [Sposoby lokalizowania zestawów przez środowisko uruchomieniowe](../deployment/how-the-runtime-locates-assemblies.md)
- [Konfigurowanie aplikacji](../configure-apps/index.md)
- [Współdziałanie z kodem niezarządzanym](../interop/index.md)
- [Zestawy w środowisku .NET](index.md)

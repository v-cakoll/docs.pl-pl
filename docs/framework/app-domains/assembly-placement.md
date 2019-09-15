---
title: Umieszczanie zestawu
ms.date: 03/30/2017
helpviewer_keywords:
- <codeBase> element
- locating assemblies
- assemblies [.NET Framework], placement
- assemblies [.NET Framework], location
ms.assetid: ff8d48bc-f606-484f-9fe1-d0af264269fb
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 829aa80169319b67a8cc5ee39fee9214cd4fcbce
ms.sourcegitcommit: 7b1ce327e8c84f115f007be4728d29a89efe11ef
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/13/2019
ms.locfileid: "70971637"
---
# <a name="assembly-placement"></a>Umieszczanie zestawu
W przypadku większości aplikacji .NET Framework można zlokalizować zestawy, które tworzą aplikację w katalogu aplikacji, w podkatalogu katalogu aplikacji lub w globalnej pamięci podręcznej zestawów (Jeśli zestaw jest udostępniony). Można przesłonić, gdzie środowisko uruchomieniowe języka wspólnego szuka zestawu przy użyciu [ \<kodu bazowej >](../../framework/configure-apps/file-schema/runtime/codebase-element.md) w pliku konfiguracyjnym. Jeśli zestaw nie ma silnej nazwy, lokalizacja określona przy użyciu [ \<bazowej kodu > element](../../framework/configure-apps/file-schema/runtime/codebase-element.md) jest ograniczone do katalogu aplikacji lub podkatalogu. Jeśli zestaw ma silną nazwę, [ \<baza kodu > element](../../framework/configure-apps/file-schema/runtime/codebase-element.md) może określić dowolną lokalizację na komputerze lub w sieci.  
  
 Podobne reguły dotyczą lokalizowania zestawów podczas pracy z niezarządzanym kodem lub aplikacjami międzyoperacyjnymi modelu COM: Jeśli zestaw będzie współużytkowany przez wiele aplikacji, powinien być zainstalowany w globalnej pamięci podręcznej zestawów. Zestawy używane z kodem niezarządzanym muszą zostać wyeksportowane jako biblioteka typów i zarejestrowane. Zestawy używane przez międzyoperacyjność modelu COM muszą być zarejestrowane w wykazie, chociaż w niektórych przypadkach ta rejestracja odbywa się automatycznie.  
  
## <a name="see-also"></a>Zobacz także

- [Sposoby lokalizowania zestawów przez środowisko uruchomieniowe](../../framework/deployment/how-the-runtime-locates-assemblies.md)
- [Konfigurowanie aplikacji](../../../docs/framework/configure-apps/index.md)
- [Współdziałanie z kodem niezarządzanym](../../../docs/framework/interop/index.md)
- [Zestawy w środowisku .NET](index.md)

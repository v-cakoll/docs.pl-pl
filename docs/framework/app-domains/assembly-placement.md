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
ms.openlocfilehash: c6a10a896494304b9c3c17bc320464a8273e430d
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/03/2018
ms.locfileid: "32752133"
---
# <a name="assembly-placement"></a>Umieszczanie zestawu
Dla większości aplikacji .NET Framework można zlokalizować zestawów, które tworzą aplikację w katalogu aplikacji, w podkatalogu w katalogu aplikacji lub w globalnej pamięci podręcznej zestawów (Jeśli zestaw jest udostępniana). Można zastąpić, gdy środowisko uruchomieniowe języka wspólnego szuka zestawu, za pomocą [ \<codeBase > elementu](../../../docs/framework/configure-apps/file-schema/runtime/codebase-element.md) w pliku konfiguracji. Jeśli zestaw nie ma silnej nazwy, lokalizacji określonej za pomocą [ \<codeBase > Element](../../../docs/framework/configure-apps/file-schema/runtime/codebase-element.md) jest ograniczona do katalogu aplikacji lub podkatalogu. Jeśli zestaw ma silną nazwę [ \<codeBase > Element](../../../docs/framework/configure-apps/file-schema/runtime/codebase-element.md) mogą określić dowolną lokalizację, na komputerze lub w sieci.  
  
 Podobne reguły mają zastosowanie do lokalizowania zestawów podczas pracy z kodem niezarządzanym lub aplikacje międzyoperacyjne COM: Jeśli zestaw zostaną udostępnione przez wiele aplikacji, powinien być zainstalowany w globalnej pamięci podręcznej zestawów. Zestawy używane z kodem niezarządzanym musi być eksportowane jako biblioteki typów i zarejestrowany. Zestawy używane przez współdziałanie z COM musi być zarejestrowany w wykazie, chociaż w niektórych przypadkach rejestracja odbywa się automatycznie.  
  
## <a name="see-also"></a>Zobacz też  
 [Sposoby lokalizowania zestawów przez środowisko uruchomieniowe](../../../docs/framework/deployment/how-the-runtime-locates-assemblies.md)  
 [Konfigurowanie aplikacji](../../../docs/framework/configure-apps/index.md)  
 [Współdziałanie COM zaawansowane](http://msdn.microsoft.com/library/3ada36e5-2390-4d70-b490-6ad8de92f2fb)  
 [Zestawy w środowisku uruchomieniowym CLR](../../../docs/framework/app-domains/assemblies-in-the-common-language-runtime.md)

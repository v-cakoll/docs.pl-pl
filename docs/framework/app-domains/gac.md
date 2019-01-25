---
title: Global Assembly Cache
ms.date: 03/30/2017
helpviewer_keywords:
- assemblies [.NET Framework], global assembly cache
- GAC (global assembly cache)
- ACLs [.NET Framework]
- global assembly cache
- cache [.NET Framework], global assembly cache
- global assembly cache, about
- access control lists [.NET Framework]
ms.assetid: cf5eacd0-d3ec-4879-b6da-5fd5e4372202
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 15b258f0392275ffd18c52d11df3bc266a55ce3f
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54566297"
---
# <a name="global-assembly-cache"></a>Global Assembly Cache
Każdy komputer, na którym zainstalowano środowisko uruchomieniowe języka wspólnego zawiera pamięć podręczna kodu komputera o nazwie Global Assembly Cache. Global Assembly Cache przechowuje zestawy specjalnie na potrzeby być współużytkowane przez wiele aplikacji na komputerze.  
  
 Należy udostępnianie zestawów poprzez instalowanie ich w globalnej pamięci podręcznej zestawów, tylko wtedy, gdy jest to konieczne. Ogólną wytyczną iż zależności zestawów, a zestawy należy umieszczać w katalogu aplikacji, chyba że współużytkowanie zestawu jest wyraźnie wymagane. Ponadto nie jest konieczne instalowanie zestawów w globalnej pamięci podręcznej zestawów, aby udostępnić je do COM interop lub niezarządzanego kodu.  
  
> [!NOTE]
>  Istnieją scenariusze, w którym możesz jawnie nie chcesz instalować zestawów w globalnej pamięci podręcznej zestawów. Jeśli umieścisz jednego z zestawów tworzących aplikację w globalnej pamięci podręcznej zestawów, może już replikacji lub zainstalować aplikację przy użyciu **xcopy** polecenie, aby skopiować katalog aplikacji. Musisz przenieść zestawu w globalnej pamięci podręcznej zestawów także.  
  
 Istnieją dwa sposoby wdrożyć zestaw w globalnej pamięci podręcznej zestawów:  
  
-   Skorzystaj z Instalatora, przeznaczony do pracy z globalnej pamięci podręcznej zestawów. To jest preferowaną opcją do instalowania zestawów w globalnej pamięci podręcznej zestawów.  
  
-   Użyj narzędzia dla deweloperów, o nazwie [narzędzia Globalna pamięć podręczna zestawów (Gacutil.exe)](../../../docs/framework/tools/gacutil-exe-gac-tool.md), podana przez [!INCLUDE[winsdklong](../../../includes/winsdklong-md.md)].  
  
    > [!NOTE]
    >  W scenariuszach wdrażania przy użyciu Instalatora Windows instalować zestawów w globalnej pamięci podręcznej zestawów. Narzędzie Global Assembly Cache tylko w scenariuszach programowania, ponieważ nie dostarcza zliczanie odwołań zestawu i inne funkcje podany przy wywołaniu metody przy użyciu Instalatora Windows.  
  
 Począwszy od programu .NET Framework 4 jest domyślną lokalizacją Global Assembly Cache **%windir%\Microsoft.NET\assembly**. We wcześniejszych wersjach programu .NET Framework, domyślna lokalizacja to **%windir%\assembly**.  
  
 Administratorzy często chronią główny katalog systemowy do zapisu i wykonywania dostępu za pomocą listy kontroli dostępu (ACL). Ponieważ globalnej pamięci podręcznej zestawów jest instalowany w podkatalogu katalogu systemowym, dziedziczy listę kontroli dostępu tego katalogu. Zaleca się, że tylko użytkownicy z uprawnieniami administratora mogła usunąć pliki z globalnej pamięci podręcznej zestawów.  
  
 Zestawy wdrożony w globalnej pamięci podręcznej zestawów, musi mieć silną nazwę. Gdy zestaw zostanie dodany do globalnej pamięci podręcznej zestawów, sprawdzania integralności są wykonywane na wszystkie pliki wchodzące w skład zestawu. Pamięć podręczna wykonuje te sprawdzania integralności, aby upewnić się, że zestaw nie został zmodyfikowany, na przykład, jeśli plik został zmieniony, ale manifest nie odzwierciedla zmianę.  
  
## <a name="see-also"></a>Zobacz także
- [Zestawy w środowisku uruchomieniowym CLR](../../../docs/framework/app-domains/assemblies-in-the-common-language-runtime.md)
- [Praca z zestawami i globalną pamięcią podręczną zestawów](../../../docs/framework/app-domains/working-with-assemblies-and-the-gac.md)
- [Zestawy o silnych nazwach](../../../docs/framework/app-domains/strong-named-assemblies.md)

---
title: Global Assembly Cache
description: Zapoznaj się z globalną pamięcią podręczną zestawów, która jest pamięcią podręczną kodu całego komputera, w której jest zainstalowany środowisko uruchomieniowe języka wspólnego dla platformy .NET.
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
ms.openlocfilehash: 7f08bb4cf279924b12432f259dae8ce5a8474285
ms.sourcegitcommit: 1c37a894c923bea021a3cc38ce7cba946357bbe1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/19/2020
ms.locfileid: "85104913"
---
# <a name="global-assembly-cache"></a>Global Assembly Cache
Każdy komputer, na którym jest zainstalowany środowisko uruchomieniowe języka wspólnego, ma pamięć podręczną kodu całego komputera o nazwie globalna pamięć podręczna zestawów. Globalna pamięć podręczna zestawów przechowuje zestawy specjalnie wyznaczonych do współużytkowania przez kilka aplikacji na komputerze.  
  
 Zestawy należy udostępniać, instalując je w globalnej pamięci podręcznej zestawów tylko wtedy, gdy jest to konieczne. Ogólnie rzecz biorąc, Zachowaj zależności zestawów jako prywatne i lokalizowanie zestawów w katalogu aplikacji, o ile udostępnianie zestawu nie jest jawnie wymagane. Ponadto nie trzeba instalować zestawów w globalnej pamięci podręcznej zestawów, aby umożliwić ich dostęp do międzyoperacyjności modelu COM lub kodu niezarządzanego.  
  
> [!NOTE]
> Istnieją scenariusze, w których jawnie nie trzeba instalować zestawu w globalnej pamięci podręcznej zestawów. W przypadku umieszczenia jednego z zestawów, które tworzą aplikację w globalnej pamięci podręcznej zestawów, nie można już replikować ani instalować aplikacji przy użyciu polecenia **xcopy** w celu skopiowania katalogu aplikacji. Należy również przenieść zestaw w globalnej pamięci podręcznej zestawów.  
  
 Istnieją dwa sposoby wdrożenia zestawu w globalnej pamięci podręcznej zestawów:  
  
- Użyj Instalatora zaprojektowanego do pracy z globalną pamięcią podręczną zestawów. Jest to preferowana opcja instalowania zestawów w globalnej pamięci podręcznej zestawów.  
  
- Użyj narzędzia deweloperskiego o nazwie [globalne narzędzie pamięci podręcznej zestawów (Gacutil.exe)](../tools/gacutil-exe-gac-tool.md), dostarczone przez Windows SDK.  
  
    > [!NOTE]
    > W scenariuszach wdrażania należy użyć Instalator Windows, aby zainstalować zestawy w globalnej pamięci podręcznej zestawów. Narzędzia globalnej pamięci podręcznej zestawów można używać tylko w scenariuszach deweloperskich, ponieważ nie zapewnia to zliczania odwołań do zestawów i innych funkcji dostępnych podczas korzystania z Instalator Windows.  
  
 Począwszy od .NET Framework 4, domyślną lokalizacją globalnej pamięci podręcznej zestawów jest **%windir%\Microsoft.NET\assembly**. We wcześniejszych wersjach .NET Framework domyślną lokalizacją jest **%windir%\assembly**.  
  
 Administratorzy często chronią katalog główny_katalog_systemowy przy użyciu listy kontroli dostępu (ACL) w celu kontrolowania dostępu do zapisu i wykonywania. Ponieważ globalna pamięć podręczna zestawów jest instalowana w podkatalogu katalogu główny_katalog_systemowy, dziedziczy listę ACL tego katalogu. Zaleca się, aby tylko użytkownicy z uprawnieniami administratora mogli usuwać pliki z globalnej pamięci podręcznej zestawów.  
  
 Zestawy wdrożone w globalnej pamięci podręcznej zestawów muszą mieć silną nazwę. Po dodaniu zestawu do globalnej pamięci podręcznej zestawów sprawdzane są wszystkie pliki wchodzące w skład zestawu. Pamięć podręczna wykonuje te operacje sprawdzania integralności, aby upewnić się, że zestaw nie został naruszony, na przykład wtedy, gdy plik został zmieniony, ale manifest nie odzwierciedla zmiany.  
  
## <a name="see-also"></a>Zobacz też

- [Zestawy w środowisku .NET](../../standard/assembly/index.md)
- [Praca z zestawami i globalną pamięcią podręczną zestawów](working-with-assemblies-and-the-gac.md)
- [Zestawy o silnych nazwach](../../standard/assembly/strong-named.md)

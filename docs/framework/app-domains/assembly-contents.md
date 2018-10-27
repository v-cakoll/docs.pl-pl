---
title: Zawartość zestawu
ms.date: 03/30/2017
helpviewer_keywords:
- assemblies [.NET Framework], multifile
- assemblies [.NET Framework], single-file
- single-file assemblies
- multifile assemblies
ms.assetid: 28116714-da77-45f7-826d-fa035d121948
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 1aed7e1e9e85f746c4b55b10c59dd82e85565b00
ms.sourcegitcommit: c93fd5139f9efcf6db514e3474301738a6d1d649
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/27/2018
ms.locfileid: "50194842"
---
# <a name="assembly-contents"></a>Zawartość zestawu
Ogólnie rzecz biorąc statyczny zestaw może składać się z czterech elementów:  
  
-   [Manifestu zestawu](../../../docs/framework/app-domains/assembly-manifest.md), który zawiera metadane zestawu.  
  
-   Metadane typu.  
  
-   Kod języka Microsoft Intermediate Language (MSIL) firmy Microsoft, który implementuje typy.  
  
-   Zestaw zasobów.  
  
 Wymagany jest jedynie manifestu zestawu, ale aby zestaw posiadał znaczące funkcje potrzebne będą typy lub zasoby.  
  
 Istnieje kilka sposobów na grupowanie tych elementów w zestawie. Można grupować wszystkie elementy w jednym fizycznym pliku, który jest pokazany na poniższej ilustracji.  
  
 ![MyAssembly.dll](../../../docs/framework/app-domains/media/assemblyover1.gif "assemblyover1")  
Zestaw jednoplikowy  
  
 Alternatywnie elementy zestawu mogą być zawarte w kilku plikach. Pliki te mogą być modułami skompilowanego kodu (.netmodule), zasobami (takimi jak pliki .bmp lub .jpg), lub innymi plikami wymaganymi przez tę aplikację. Należy utworzyć zestaw wieloplikowy gdy zajdzie potrzeba połączenia modułów napisanych w różnych językach oraz optymalizacji pobierania aplikacji poprzez umieszczenie rzadko używanych typów w module, który jest pobierany tylko w razie potrzeby.  
  
 Na poniższej ilustracji Deweloper hipotetycznej aplikacji zdecydował się oddzielić część kodu narzędziowego do innego modułu i zachować duży plik zasobów (w tym przypadku obraz .bmp) w jego oryginalnym pliku. .NET Framework pobiera plik tylko wtedy, gdy istnieje do niego odwołanie; przechowywanie rzadko używanego kodu w osobnym pliku niż aplikacja optymalizuje pobieranie kodu.  
  
 ![MyAssembly.dll](../../../docs/framework/app-domains/media/assemblyover2.gif "assemblyover2")  
Zestaw wieloplikowy  
  
> [!NOTE]
>  Pliki z których składają się wieloplikowe zestawy nie są fizycznie połączone przez system plików. Przeciwnie, są one połączone za pośrednictwem manifestu zestawu i aparatu plików wykonywalnych języka wspólnego zarządza nimi osobno.  
  
 Na tej ilustracji wszystkie trzy pliki należą do zestawu, zgodnie z opisem w manifeście zestawu zawartym w MyAssembly.dll. Dla systemu plików są to trzy oddzielne pliki. Należy zauważyć, że plik Util.netmodule został skompilowany jako moduł, ponieważ nie zawiera żadnych informacji zestawu. Podczas tworzenia zestawu, manifest zestawu został dodany do MyAssembly.dll, wskazując na jego relację z Util.netmodule i Graphic.bmp.  
  
 Obecnie podczas projektowania kodu źródłowego, należy podejmować jawne decyzje dotyczące partycji funkcje aplikacji w jeden lub więcej plików. Podczas projektowania kodu .NET Framework, podejmiesz podobne decyzje, o tym jak podzielić funkcjonalności, tworząc jeden lub więcej zestawów.  
  
## <a name="see-also"></a>Zobacz też  
- [Zestawy w środowisku uruchomieniowym CLR](../../../docs/framework/app-domains/assemblies-in-the-common-language-runtime.md)  
- [Manifest zestawu](../../../docs/framework/app-domains/assembly-manifest.md)  
- [Zagadnienia dotyczące zabezpieczeń zestawów](../../../docs/framework/app-domains/assembly-security-considerations.md)

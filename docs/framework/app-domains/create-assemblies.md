---
title: Tworzenie zestawów
ms.date: 03/30/2017
helpviewer_keywords:
- assemblies [.NET Framework], multifile
- single-file assemblies
- assemblies [.NET Framework], creating
- multifile assemblies
ms.assetid: 54832ee9-dca8-4c8b-913c-c0b9d265e9a4
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 8490351b4ab1bb115e4bd7277f43ad22b144a2df
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/03/2018
ms.locfileid: "32752068"
---
# <a name="creating-assemblies"></a>Tworzenie zestawów
Możesz utworzyć zestawy jednoplikowe lub wiele plików przy użyciu IDE, takich jak [!INCLUDE[vsprvslong](../../../includes/vsprvslong-md.md)], lub kompilatory i narzędzi dostarczonych przez [!INCLUDE[winsdklong](../../../includes/winsdklong-md.md)]. Najprostsza zestaw jest pojedynczy plik ma prostą nazwą, który jest ładowany do domeny pojedynczej aplikacji. Ten zestaw nie może odwoływać się do innych zestawów znajdujących się poza katalogiem aplikacji i nie podlegają kontroli wersji. Aby odinstalować aplikację, składa się z zestawu, po prostu Usuń katalog, w którym znajduje się. W przypadku wielu deweloperów zestawu z tych funkcji jest wszystkie, który jest wymagany do wdrażania aplikacji.  
  
 Można utworzyć zestawu wieloplikowego z wielu modułów kodu i pliki zasobów. Istnieje również możliwość utworzenia zestawu, który może być współużytkowane przez wiele aplikacji. Zestaw udostępnionego musi mieć silnej nazwy i może zostać wdrożony w globalnej pamięci podręcznej zestawów.  
  
 Istnieje kilka opcji, jeśli grupowanie moduły kodu i zasobów w zestawy, w zależności od następujących czynników:  
  
-   Przechowywanie wersji  
  
     Moduły grupy, które powinny mieć tego samego informacje o wersji.  
  
-   wdrażania  
  
     Moduły kodu grupy i zasobów, które obsługują modelu wdrożenia.  
  
-   Ponowne użycie  
  
     Grupy modułów, jeśli logicznie użyciem ze sobą w celu niektóre. Zestaw typów i klasy rzadko używane do obsługi programu można na przykład umieścić w tym samym zestawie. Ponadto typy, które mają być udostępniane wielu aplikacji powinny zostać utworzone w zestawie i zestaw powinny być podpisane przy użyciu silnej nazwy.  
  
-   Zabezpieczenia  
  
     Grupa modułów zawierających typy, które wymagają tych samych uprawnień zabezpieczeń.  
  
-   Określanie zakresu  
  
     Grupa modułów zawierających typy, których widoczność powinna być ograniczona do tego samego zestawu.  
  
 Podczas udostępniania języka wspólnego zestawy środowiska wykonawczego niezarządzanych aplikacji modelu COM, muszą być wprowadzane uwagi. Aby uzyskać więcej informacji na temat pracy z kodem niezarządzanym, zobacz [udostępnianie składników .NET Framework modelowi COM](../../../docs/framework/interop/exposing-dotnet-components-to-com.md).  
  
## <a name="see-also"></a>Zobacz też  
 [Programowanie za pomocą zestawów](../../../docs/framework/app-domains/programming-with-assemblies.md)  
 [Przechowywanie wersji zestawu](../../../docs/framework/app-domains/assembly-versioning.md)  
 [Instrukcje: kompilacja zestawu jednoplikowego](../../../docs/framework/app-domains/how-to-build-a-single-file-assembly.md)  
 [Instrukcje: kompilacja zestawów wieloplikowych](../../../docs/framework/app-domains/how-to-build-a-multifile-assembly.md)  
 [Sposoby lokalizowania zestawów przez środowisko uruchomieniowe](../../../docs/framework/deployment/how-the-runtime-locates-assemblies.md)  
 [Zestawy wieloplikowe](../../../docs/framework/app-domains/multifile-assemblies.md)

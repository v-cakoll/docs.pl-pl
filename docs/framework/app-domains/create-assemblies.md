---
title: "Tworzenie zestawów"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-bcl
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- assemblies [.NET Framework], multifile
- single-file assemblies
- assemblies [.NET Framework], creating
- multifile assemblies
ms.assetid: 54832ee9-dca8-4c8b-913c-c0b9d265e9a4
caps.latest.revision: "8"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: f5aa4b8fa5422ae126a6027c5fe3358925873782
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
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
 [Porady: tworzenie zestawów pojedynczego pliku](../../../docs/framework/app-domains/how-to-build-a-single-file-assembly.md)  
 [Porady: kompilacja zestawów wieloplikowych](../../../docs/framework/app-domains/how-to-build-a-multifile-assembly.md)  
 [Jak lokalizuje zestawów przez środowisko uruchomieniowe](../../../docs/framework/deployment/how-the-runtime-locates-assemblies.md)  
 [Zestawy wieloplikowe](../../../docs/framework/app-domains/multifile-assemblies.md)

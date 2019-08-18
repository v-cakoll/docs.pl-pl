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
ms.openlocfilehash: 314a94be140b392964951299fba2fed4ac7e6e68
ms.sourcegitcommit: 29a9b29d8b7d07b9c59d46628da754a8bff57fa4
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/17/2019
ms.locfileid: "69566792"
---
# <a name="creating-assemblies"></a>Tworzenie zestawów

Można tworzyć zestawy Jednoplikowe lub wieloplikowe za pomocą IDE, takie jak Visual Studio, lub kompilatory i narzędzia dostarczone przez Windows SDK. Najprostszym zestawem jest pojedynczy plik, który ma prostą nazwę i jest ładowany do pojedynczej domeny aplikacji. Ten zestaw nie może odwoływać się do innych zestawów poza katalogiem aplikacji i nie jest sprawdzany Sprawdzanie wersji. Aby odinstalować aplikację utworzoną z zestawu, wystarczy usunąć znajdujący się w niej katalog. W przypadku wielu deweloperów zestaw z tymi funkcjami jest wymagany do wdrożenia aplikacji.

Zestaw wieloplikowy można utworzyć z kilku modułów kodu i plików zasobów. Możesz również utworzyć zestaw, który może być współużytkowany przez wiele aplikacji. Zestaw współużytkowany musi mieć silną nazwę i można go wdrożyć w globalnej pamięci podręcznej zestawów.

Istnieje kilka opcji grupowania modułów kodu i zasobów w zestawy, w zależności od następujących czynników:

- Przechowywanie wersji

     Grupuj moduły, które powinny mieć te same informacje o wersji.

- wdrażania

     Grupuj moduły kodu i zasoby, które obsługują model wdrażania.

- Było

     Grupuj moduły, jeśli mogą być logicznie używane razem do pewnego celu. Na przykład zestaw składający się z typów i klas używanych rzadko do konserwacji programu można umieścić w tym samym zestawie. Ponadto typy, które mają być współużytkowane z wieloma aplikacjami, powinny być pogrupowane w zestaw, a zestaw powinien być podpisany za pomocą silnej nazwy.

- Zabezpieczenia

     Moduły grupy zawierające typy, które wymagają tych samych uprawnień zabezpieczeń.

- Zakresów

     Moduły grupy zawierające typy, których widoczność powinna być ograniczona do tego samego zestawu.

Przed udostępnieniem zestawów środowiska uruchomieniowego języka wspólnego dla niezarządzanych aplikacji COM należy uwzględnić specjalne zagadnienia. Aby uzyskać więcej informacji na temat pracy z kodem niezarządzanym, zobacz [Udostępnianie składników .NET Framework do modelu COM](../../../docs/framework/interop/exposing-dotnet-components-to-com.md).

## <a name="see-also"></a>Zobacz także

- [Programowanie za pomocą zestawów](../../../docs/framework/app-domains/programming-with-assemblies.md)
- [Przechowywanie wersji zestawu](../../../docs/framework/app-domains/assembly-versioning.md)
- [Instrukcje: Kompilowanie zestawu jednoplikowego](../../../docs/framework/app-domains/how-to-build-a-single-file-assembly.md)
- [Instrukcje: Kompilowanie zestawu wieloplikowego](../../../docs/framework/app-domains/how-to-build-a-multifile-assembly.md)
- [Sposoby lokalizowania zestawów przez środowisko uruchomieniowe](../../../docs/framework/deployment/how-the-runtime-locates-assemblies.md)
- [Zestawy wieloplikowe](../../../docs/framework/app-domains/multifile-assemblies.md)

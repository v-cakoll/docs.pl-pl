---
title: Tworzenie zestawów
ms.date: 08/19/2019
helpviewer_keywords:
- assemblies [.NET Framework], multifile
- single-file assemblies
- assemblies [.NET Framework], creating
- multifile assemblies
ms.assetid: 54832ee9-dca8-4c8b-913c-c0b9d265e9a4
ms.openlocfilehash: 81fffb2b2e1d56d6068bf6f663a13fad6968a383
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/15/2020
ms.locfileid: "73740510"
---
# <a name="create-assemblies"></a>Tworzenie zestawów

Można tworzyć zestawy jednoplikowe lub wieloplikowe przy użyciu ide, takich jak Visual Studio lub kompilatorów i narzędzi dostarczonych przez zestaw Windows SDK. Najprostszy zestaw jest pojedynczy plik, który ma prostą nazwę i jest ładowany do jednej domeny aplikacji. Do tego zestawu nie mogą odwoływać się inne zestawy poza katalogiem aplikacji i nie są poddawane sprawdzaniu wersji. Aby odinstalować aplikację składającą się z zestawu, wystarczy usunąć katalog, w którym się znajduje. Dla wielu deweloperów zestaw z tymi funkcjami jest wszystko, co jest potrzebne do wdrożenia aplikacji.

Można utworzyć zestaw wieloplikowy z kilku modułów kodu i plików zasobów. Można również utworzyć zestaw, który może być współużytkowany przez wiele aplikacji. Zestaw udostępniony musi mieć silną nazwę i może być wdrożony w globalnej pamięci podręcznej zestawów.

Podczas grupowania modułów kodu i zasobów w zestawy dostępnych jest kilka opcji, w zależności od następujących czynników:

- Obsługa wersji

     Grupuj moduły, które powinny mieć te same informacje o wersji.

- Wdrożenie

     Grupuj moduły kodu i zasoby, które obsługują model wdrażania.

- Ponowne użycie

     Grupuj moduły, jeśli mogą być logicznie używane razem do pewnego celu. Na przykład zestaw składający się z typów i klas rzadko używanych do konserwacji programu można umieścić w tym samym zestawie. Ponadto typy, które mają być udostępniane z wieloma aplikacjami powinny być pogrupowane w zestaw i zestaw powinien być podpisany o silnej nazwie.

- Zabezpieczenia

     Grupuj moduły zawierające typy, które wymagają tych samych uprawnień zabezpieczeń.

- Zakresu

     Grupuj moduły zawierające typy, których widoczność powinna być ograniczona do tego samego zestawu.

Istnieją szczególne zagadnienia podczas udostępniania zestawów w czasie wykonywania języka wspólnego dla niezarządzanych aplikacji COM. Aby uzyskać więcej informacji na temat pracy z kodem niezarządzanym, zobacz [Udostępnianie składników .NET Framework do com](../../framework/interop/exposing-dotnet-components-to-com.md).

## <a name="see-also"></a>Zobacz też

- [Przechowywanie wersji zestawu](versioning.md)
- [Jak: Tworzenie zestawu pojedynczego pliku](../../framework/app-domains/build-single-file-assembly.md)
- [Jak: Tworzenie zestawu wieloplikowego](../../framework/app-domains/build-multifile-assembly.md)
- [Jak program runtime lokalizuje zestawy](../../framework/deployment/how-the-runtime-locates-assemblies.md)
- [Zestawy wieloplikowe](../../framework/app-domains/multifile-assemblies.md)

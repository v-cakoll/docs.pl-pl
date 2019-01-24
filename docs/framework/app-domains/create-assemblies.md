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
ms.openlocfilehash: 2713011d61b41dfa4d72a635c656c0c00cb42f8d
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54643614"
---
# <a name="creating-assemblies"></a>Tworzenie zestawów

Można utworzyć pojedynczy plik lub wieloplikowe zestawy w środowisku IDE, takie jak Visual Studio lub z kompilatorów i narzędzi dostarczonych przez [!INCLUDE[winsdklong](../../../includes/winsdklong-md.md)]. Najprostsza zestaw jest pojedynczy plik o nazwie prostego, który jest ładowany do domeny pojedynczej aplikacji. Ten zestaw nie może być przywoływany przez inne zestawy poza katalogiem aplikacji i nie podlegają kontroli wersji. Aby odinstalować aplikację składają się z zestawu, po prostu usunąć katalogu, w którym znajduje się. W przypadku wielu programistów zestawu za pomocą tych funkcji jest wszystko, co jest potrzebne do wdrożenia aplikacji.

Możesz utworzyć zestaw wieloplikowy z kilku modułów kodu i pliki zasobów. Można również utworzyć zestaw, który może być współużytkowany przez wiele aplikacji. Zestaw współużytkowany musi mieć silną nazwę i można je wdrożyć w globalnej pamięci podręcznej.

Istnieje kilka opcji, gdy grupowanie modułów kodu i zasoby do zestawów, w zależności od następujących czynników:

-   Obsługa wersji

     Moduły grupy, które powinny mieć te same informacje o wersji.

-   wdrażania

     Moduły kodu grupy i zasobów, które obsługują model wdrożenia.

-   Ponowne użycie

     Grupy modułów, jeśli one logicznie można ze sobą w celu niektóre. Na przykład zestaw składający się z typów i klas, rzadko używane dla programu obsługi można umieścić w tym samym zestawie. Ponadto typy, które ma być współużytkowany z wieloma aplikacjami powinny zostać utworzone do zestawu i zestawu powinna być podpisany silną nazwą.

-   Zabezpieczenia

     Grupy modułów zawierających typy, które wymagają tych samych uprawnień zabezpieczeń.

-   Wyznaczanie zakresu

     Grupy modułów zawierających typy, których widoczność powinno zostać ograniczone do tego samego zestawu.

Podczas udostępniania języka wspólnego zestawów środowiska uruchomieniowego do niezarządzanych aplikacji modelu COM, można wprowadzać uwagi. Aby uzyskać więcej informacji na temat pracy z kodem niezarządzanym, zobacz [udostępnianie składników .NET Framework modelowi COM](../../../docs/framework/interop/exposing-dotnet-components-to-com.md).

## <a name="see-also"></a>Zobacz także

- [Programowanie za pomocą zestawów](../../../docs/framework/app-domains/programming-with-assemblies.md)
- [Przechowywanie wersji zestawu](../../../docs/framework/app-domains/assembly-versioning.md)
- [Instrukcje: Kompilacja zestawów pojedynczego pliku](../../../docs/framework/app-domains/how-to-build-a-single-file-assembly.md)
- [Instrukcje: Kompilacja zestawów wieloplikowych](../../../docs/framework/app-domains/how-to-build-a-multifile-assembly.md)
- [Sposoby lokalizowania zestawów przez środowisko uruchomieniowe](../../../docs/framework/deployment/how-the-runtime-locates-assemblies.md)
- [Zestawy wieloplikowe](../../../docs/framework/app-domains/multifile-assemblies.md)
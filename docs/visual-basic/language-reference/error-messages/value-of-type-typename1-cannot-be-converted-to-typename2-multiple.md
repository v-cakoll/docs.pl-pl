---
title: Wartości typu „<typename1>” nie może zostać przekonwertowana na „<typename2>” (Odwołania do wielu plików)
ms.date: 07/20/2015
f1_keywords:
- vbc30961
- bc30961
helpviewer_keywords:
- BC30961
ms.assetid: 8be5aa0d-d236-4ac3-aa9c-5044f9f6562b
ms.openlocfilehash: 58b334eb5e6db443bcfaba72729d59cb1d798e70
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/18/2019
ms.locfileid: "58833532"
---
# <a name="value-of-type-typename1-cannot-be-converted-to-typename2-multiple-file-references"></a>Wartość typu "\<typename1 >" nie można przekonwertować na "\<typename2 >" (odwołania do wielu plików)
Wartość typu "\<typename1 >" nie można przekonwertować na "\<typename2 >". Niezgodność typów przyczyną może być połączenie odwołania pliku do "\<filepath1 >' w projekcie"\<projectname1 > "z odwołaniem do pliku"\<filepath2 >' w projekcie "\<projectname2 >". Jeśli oba zestawy są identyczne, spróbuj wymienić te odwołania, tak aby oba odwołania z tej samej lokalizacji.  
  
 W sytuacji, gdy projekt sprawia, że więcej niż jedno odwołanie pliku do zestawu kompilator nie może zagwarantować, że jeden typ może być konwertowany na inny.  
  
 Odwołanie do każdego pliku Określa ścieżkę i nazwę pliku dla pliku wyjściowego projektu (zwykle w pliku DLL). Kompilator nie może zagwarantować, że pliki wyjściowe pochodzą z tego samego źródła lub fakt, że reprezentują tę samą wersję tego samego zestawu. W związku z tym nie gwarantuje, że typy w różne odwołania są tego samego typu lub nawet ten. mogą być konwertowane do drugiego.  
  
 Odwołanie do pojedynczego pliku można użyć, jeśli wiesz, że zestawy występujące w odwołaniach mają taką samą tożsamość zestawu. *Tożsamości zestawu* zawiera nazwę zestawu, wersji, klucz publiczny, jeśli istnieje i kultury. Te informacje w sposób unikatowy identyfikuje zestaw.  
  
 **Identyfikator błędu:** BC30961  
  
## <a name="to-correct-this-error"></a>Aby poprawić ten błąd  
  
-   Jeśli zestawy występujące w odwołaniach ma taką samą tożsamość zestawu, usuń lub Zamień jednego odwołania do pliku, tak, aby istniała tylko odwołanie do pojedynczego pliku.  
  
-   Jeśli zestawy występujące w odwołaniach nie ma tej samej tożsamości zestawu, a następnie zmień swój kod, tak aby nie próbuje przekonwertować typu na jeden typ w innym.  
  
## <a name="see-also"></a>Zobacz także

- [Konwersje typów w języku Visual Basic](../../../visual-basic/programming-guide/language-features/data-types/type-conversions.md)
- [Zarządzanie odwołaniami w projekcie](/visualstudio/ide/managing-references-in-a-project)

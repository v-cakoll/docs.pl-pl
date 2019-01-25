---
title: Wartości typu &#39; &lt;typename1&gt; &#39; nie można przekonwertować na &#39; &lt;typename2&gt; &#39; (odwołania do wielu plików)
ms.date: 07/20/2015
f1_keywords:
- vbc30961
- bc30961
helpviewer_keywords:
- BC30961
ms.assetid: 8be5aa0d-d236-4ac3-aa9c-5044f9f6562b
ms.openlocfilehash: 943b9612a9217b90c19f34285e812c4e1cccf81a
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54691378"
---
# <a name="value-of-type-39lttypename1gt39-cannot-be-converted-to-39lttypename2gt39-multiple-file-references"></a>Wartości typu &#39; &lt;typename1&gt; &#39; nie można przekonwertować na &#39; &lt;typename2&gt; &#39; (odwołania do wielu plików)
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


---
title: Wartości typu &#39; &lt;typename1&gt; &#39; nie można przekonwertować na &#39; &lt;typename2&gt; &#39; (wiele odwołań do pliku)
ms.date: 07/20/2015
f1_keywords:
- vbc30961
- bc30961
helpviewer_keywords:
- BC30961
ms.assetid: 8be5aa0d-d236-4ac3-aa9c-5044f9f6562b
ms.openlocfilehash: 41c18160be9b546f8b525376fa06bc0eca6c117a
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33603694"
---
# <a name="value-of-type-39lttypename1gt39-cannot-be-converted-to-39lttypename2gt39-multiple-file-references"></a>Wartości typu &#39; &lt;typename1&gt; &#39; nie można przekonwertować na &#39; &lt;typename2&gt; &#39; (wiele odwołań do pliku)
Wartości typu "\<typename1 >' nie można przekonwertować na"\<typename2 > ". Niezgodność typów przyczyną może być połączenie odwołania pliku do "\<filepath1 >" w projekcie "\<projectname1 >" z odwołaniem pliku do "\<filepath2 >" w projekcie "\<projectname2 >". Jeżeli oba zestawy są identyczne, spróbuj zamienić te odwołania, tak aby oba pochodziły z tej samej lokalizacji.  
  
 W sytuacji, gdy projekt sprawia, że więcej niż jedno odwołanie pliku do zestawu kompilator nie może zagwarantować, że jeden typ można przekonwertować na inny.  
  
 Odwołanie do każdego pliku Określa ścieżkę i nazwę pliku dla pliku wyjściowego projektu (zwykle w pliku DLL). Kompilator nie może zagwarantować, że pliki wyjściowe pochodzą z tego samego źródła, lub że reprezentują tej samej wersji tego samego zestawu. W związku z tym nie może zagwarantować, że typy w różnych odwołania są tego samego typu lub nawet co można przekonwertować na innych.  
  
 Odwołanie pojedynczego pliku można użyć, jeśli wiadomo, że zestawy występujące w odwołaniach mają tej samej tożsamości zestawu. *Tożsamości zestawu* zawiera nazwę, wersję, klucz publiczny, jeśli istnieją i kultury zestawu. Te informacje w sposób unikatowy identyfikuje zestawu.  
  
 **Identyfikator błędu:** BC30961  
  
## <a name="to-correct-this-error"></a>Aby poprawić ten błąd  
  
-   Jeśli zestawów występujących w odwołaniach ma taką samą tożsamość zestawu, usuń lub Zamień jedno z odwołań pliku tak, aby tylko odwołanie do pojedynczego pliku.  
  
-   Jeśli zestawów występujących w odwołaniach nie miały tej samej tożsamości zestawu, a następnie zmień swój kod, tak aby nie próbuje przekonwertować typu w jednym z typem w innym.  
  
## <a name="see-also"></a>Zobacz też  
 [Konwersje typów w języku Visual Basic](../../../visual-basic/programming-guide/language-features/data-types/type-conversions.md)  
 [Zarządzanie odwołaniami w projekcie](/visualstudio/ide/managing-references-in-a-project)  
 

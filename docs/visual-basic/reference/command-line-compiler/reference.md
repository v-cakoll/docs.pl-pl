---
title: /reference (Visual Basic)
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- /reference compiler option [Visual Basic]
- r compiler option [Visual Basic]
- -reference compiler option [Visual Basic]
- /r compiler option [Visual Basic]
- reference compiler option [Visual Basic]
- -r compiler option [Visual Basic]
ms.assetid: 66bdfced-bbf6-43d1-a554-bc0990315737
caps.latest.revision: "16"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: f8c6851802afa818cc80b3f6d7eafc2ef47ac689
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="reference-visual-basic"></a>/reference (Visual Basic)
Powoduje, że kompilator, aby udostępnić informacje o typie w określonych zestawów do projektu, które są aktualnie kompilacji.  
  
## <a name="syntax"></a>Składnia  
  
```  
/reference:fileList  
' -or-  
/r:fileList  
```  
  
## <a name="arguments"></a>Argumenty  
  
|Termin|Definicja|  
|---|---|  
|`fileList`|Wymagany. Rozdzielana przecinkami lista nazw plików zestawu. Jeśli nazwa pliku zawiera spację, nazwę należy ująć w cudzysłów.|  
  
## <a name="remarks"></a>Uwagi  
 Pliki, które należy zaimportować musi zawierać metadane zestawu. Tylko typy publiczne są widoczne poza zestaw. [/Addmodule](../../../visual-basic/reference/command-line-compiler/addmodule.md) opcja importuje metadane z modułu.  
  
 Jeśli odwołanie do zestawu (zestawów A) które odwołuje się do innego zestawu (zestaw B), należy odwołanie do zestawu B, jeśli:  
  
-   Typ z zestawu A dziedziczy z typu lub implementuje interfejs z zestawu B.  
  
-   Pola, właściwości, zdarzenia lub metodę, która ma zwracany typ lub parametr typu z B zestawu jest wywoływany.  
  
 Użyj [/libpath](../../../visual-basic/reference/command-line-compiler/libpath.md) Aby określić katalog, w którym znajduje się co najmniej jednego odwołania do zestawów.  
  
 Dla kompilatora do rozpoznawania typu w zestawie (nie w module) należy wymusić można rozpoznać typu. Definiowanie wystąpienia typu jest przykładem jak to zrobić. Inne metody są dostępne do rozpoznania nazwy typów w zestawie dla kompilatora. Na przykład jeśli można dziedziczyć po typie w zestawie, nazwa typu następnie staje się znane do kompilatora.  
  
 Vbc.rsp plik odpowiedzi, który odwołuje się do najczęściej używanych [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)] zestawy, jest używany domyślnie. Użyj `/noconfig` Jeśli nie chcesz, aby kompilator, aby używał Vbc.rsp.  
  
 Krótka forma z `/reference` jest `/r`.  
  
## <a name="example"></a>Przykład  
 Poniższy kod tworzy plik źródłowy `Input.vb` i odwołuje się do zestawów z `Metad1.dll` i `Metad2.dll` do produkcji `Out.exe`.  
  
```  
vbc /reference:metad1.dll,metad2.dll /out:out.exe input.vb  
```  
  
## <a name="see-also"></a>Zobacz też  
 [Kompilator w wierszu polecenia programu Visual Basic](../../../visual-basic/reference/command-line-compiler/index.md)  
 [/ noconfig](../../../visual-basic/reference/command-line-compiler/noconfig.md)  
 [/ TARGET (Visual Basic)](../../../visual-basic/reference/command-line-compiler/target.md)  
 [Publiczna](../../../visual-basic/language-reference/modifiers/public.md)  
 [Kompilacja przykładów — wiersze poleceń](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)

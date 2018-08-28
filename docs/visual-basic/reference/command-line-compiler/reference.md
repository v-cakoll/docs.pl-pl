---
title: — Odwołanie (Visual Basic)
ms.date: 03/13/2018
helpviewer_keywords:
- /reference compiler option [Visual Basic]
- r compiler option [Visual Basic]
- -reference compiler option [Visual Basic]
- /r compiler option [Visual Basic]
- reference compiler option [Visual Basic]
- -r compiler option [Visual Basic]
ms.assetid: 66bdfced-bbf6-43d1-a554-bc0990315737
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: cb5d3b4c50a9c22880bdcc8406835cf51481e3cd
ms.sourcegitcommit: e614e0f3b031293e4107f37f752be43652f3f253
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/27/2018
ms.locfileid: "43003128"
---
# <a name="-reference-visual-basic"></a>— Odwołanie (Visual Basic)
Powoduje, że kompilator udostępnia informacje o typie w określonych zestawach do projektu, które są aktualnie kompilacji.  
  
## <a name="syntax"></a>Składnia  
  
```  
-reference:fileList  
' -or-  
-r:fileList  
```  
  
## <a name="arguments"></a>Argumenty  
  
|Termin|Definicja|  
|---|---|  
|`fileList`|Wymagane. Rozdzielana przecinkami lista nazw plików zestawu. Jeśli nazwa pliku zawiera spację, nazwę należy ująć w znaki cudzysłowu.|  
  
## <a name="remarks"></a>Uwagi  
 Pliki, które należy zaimportować musi zawierać metadane zestawu. Tylko typy publiczne są widoczne poza zestawem. [/Addmodule](../../../visual-basic/reference/command-line-compiler/addmodule.md) opcja importuje metadane z modułu.  
  
 Jeśli odwołujesz się zestaw (Assembly A) która sama odwołuje się do innego zestawu (Assembly B), należy odwołanie do zestawu B, jeśli:  
  
-   Typ z zestawu A dziedziczy z typu lub implementuje interfejs z zestawu B.  
  
-   Pola, właściwości, zdarzenia lub metody, która ma typ lub parametr typu zwracanego z zestawu B zostanie wywołana.  
  
 Użyj [- libpath](../../../visual-basic/reference/command-line-compiler/libpath.md) określić katalog, w którym znajduje się co najmniej jeden z odwołania do zestawów.  
  
 Aby kompilator mógł rozpoznać typu w zestawie (nie moduł) należy wymusić do rozpoznania typu. Jednym z przykładów jak to zrobić, jest definiowanie wystąpienia tego typu. Inne metody są dostępne do rozpoznawania nazw typów w zestawie dla kompilatora. Na przykład jeśli możesz dziedziczyć z typu w zestawie, nazwa typu następnie staje się znane kompilator.  
  
 Plik odpowiedzi Vbc.rsp odwołania najczęściej używanych [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)] zestawów, jest używane domyślnie. Użyj `-noconfig` Jeśli nie chcesz, aby kompilator korzystać Vbc.rsp.  
  
 Krótkiej formy `-reference` jest `/r`.  
  
## <a name="example"></a>Przykład  
 Poniższe polecenie kompiluje plik źródłowy `Input.vb` i odwoływać się do zestawów z `Metad1.dll` i `Metad2.dll` do produkcji `Out.exe`.  
  
```console
vbc -reference:metad1.dll,metad2.dll -out:out.exe input.vb  
```  
  
## <a name="see-also"></a>Zobacz też  
 [Kompilator wiersza polecenia programu Visual Basic](../../../visual-basic/reference/command-line-compiler/index.md)  
 [-noconfig](../../../visual-basic/reference/command-line-compiler/noconfig.md)  
 [-target (Visual Basic)](../../../visual-basic/reference/command-line-compiler/target.md)  
 [Public](../../../visual-basic/language-reference/modifiers/public.md)  
 [Przykłady kompilacji — wiersze poleceń](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)

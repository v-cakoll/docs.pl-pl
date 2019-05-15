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
ms.openlocfilehash: 2394a23ddd59d09ce53c78fc4486fc5bae9e8516
ms.sourcegitcommit: c7a7e1468bf0fa7f7065de951d60dfc8d5ba89f5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/14/2019
ms.locfileid: "65583362"
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
|`fileList`|Wymagana. Rozdzielana przecinkami lista nazw plików zestawu. Jeśli nazwa pliku zawiera spację, nazwę należy ująć w znaki cudzysłowu.|  
  
## <a name="remarks"></a>Uwagi  
 Pliki, które należy zaimportować musi zawierać metadane zestawu. Tylko typy publiczne są widoczne poza zestawem. [/Addmodule](../../../visual-basic/reference/command-line-compiler/addmodule.md) opcja importuje metadane z modułu.  
  
 Jeśli odwołujesz się zestaw (Assembly A) która sama odwołuje się do innego zestawu (Assembly B), należy odwołanie do zestawu B, jeśli:  
  
- Typ z zestawu A dziedziczy z typu lub implementuje interfejs z zestawu B.  
  
- Pola, właściwości, zdarzenia lub metody, która ma typ lub parametr typu zwracanego z zestawu B zostanie wywołana.  
  
 Użyj [- libpath](../../../visual-basic/reference/command-line-compiler/libpath.md) określić katalog, w którym znajduje się co najmniej jeden z odwołania do zestawów.  
  
 Aby kompilator mógł rozpoznać typu w zestawie (nie moduł) należy wymusić do rozpoznania typu. Jednym z przykładów jak to zrobić, jest definiowanie wystąpienia tego typu. Inne metody są dostępne do rozpoznawania nazw typów w zestawie dla kompilatora. Na przykład jeśli możesz dziedziczyć z typu w zestawie, nazwa typu następnie staje się znane kompilator.  
  
 Plik odpowiedzi Vbc.rsp, która odwołuje się do powszechnie stosowane zestawów .NET Framework, jest używany domyślnie. Użyj `-noconfig` Jeśli nie chcesz, aby kompilator korzystać Vbc.rsp.  
  
 Krótkiej formy `-reference` jest `/r`.  
  
## <a name="example"></a>Przykład  
 Poniższe polecenie kompiluje plik źródłowy `Input.vb` i odwoływać się do zestawów z `Metad1.dll` i `Metad2.dll` do produkcji `Out.exe`.  
  
```console
vbc -reference:metad1.dll,metad2.dll -out:out.exe input.vb  
```  
  
## <a name="see-also"></a>Zobacz także

- [Kompilator wiersza polecenia programu Visual Basic](../../../visual-basic/reference/command-line-compiler/index.md)
- [-noconfig](../../../visual-basic/reference/command-line-compiler/noconfig.md)
- [-target (Visual Basic)](../../../visual-basic/reference/command-line-compiler/target.md)
- [Public](../../../visual-basic/language-reference/modifiers/public.md)
- [Przykłady kompilacji — wiersze poleceń](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)

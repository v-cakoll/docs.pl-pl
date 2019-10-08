---
title: -Reference (Visual Basic)
ms.date: 03/13/2018
helpviewer_keywords:
- /reference compiler option [Visual Basic]
- r compiler option [Visual Basic]
- -reference compiler option [Visual Basic]
- /r compiler option [Visual Basic]
- reference compiler option [Visual Basic]
- -r compiler option [Visual Basic]
ms.assetid: 66bdfced-bbf6-43d1-a554-bc0990315737
ms.openlocfilehash: 552fbcf920be609de83708a995a87761f6080220
ms.sourcegitcommit: eff6adb61852369ab690f3f047818c90580e7eb1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/07/2019
ms.locfileid: "72005274"
---
# <a name="-reference-visual-basic"></a>-Reference (Visual Basic)
Powoduje, że kompilator udostępnia informacje o typie w określonych zestawach, które są dostępne dla aktualnie kompilowanego projektu.  
  
## <a name="syntax"></a>Składnia  
  
```console  
-reference:fileList  
```

lub

```console
-r:fileList  
```  
  
## <a name="arguments"></a>Argumenty  
  
|Termin|Definicja|  
|---|---|  
|`fileList`|Wymagany. Rozdzielana przecinkami lista nazw plików zestawu. Jeśli nazwa pliku zawiera spację, należy ująć ją w cudzysłów.|  
  
## <a name="remarks"></a>Uwagi  
 Importowane pliki muszą zawierać metadane zestawu. Tylko typy publiczne są widoczne poza zestawem. Opcja [/addmodule](../../../visual-basic/reference/command-line-compiler/addmodule.md) Importuje metadane z modułu.  
  
 Jeśli odwołujesz się do zestawu (zestawu A), który sam odwołuje się do innego zestawu (zestawu B), należy odwołać się do zestawu B, jeśli:  
  
- Typ z zestawu A dziedziczy po typie lub implementuje interfejs z zestawu B.  
  
- Wywołano pole, właściwość, zdarzenie lub metodę z typem zwracanym lub typem parametru z zestawu B.  
  
 Użyj [-LIBPATH](../../../visual-basic/reference/command-line-compiler/libpath.md) , aby określić katalog, w którym znajduje się co najmniej jedno odwołanie do zestawu.  
  
 Aby kompilator rozpoznawał typ w zestawie (nie w module), musi być zmuszony do rozpoznania typu. Przykładem tego, jak można to zrobić, jest zdefiniowanie wystąpienia typu. Inne sposoby rozpoznawania nazw typów w zestawie dla kompilatora. Na przykład, jeśli dziedziczysz z typu w zestawie, nazwa typu jest nazywana kompilatorem.  
  
 Plik odpowiedzi VBC. rsp, który odwołuje się do najczęściej używanych zestawów .NET Framework, jest używany domyślnie. Użyj `-noconfig`, jeśli nie chcesz, aby kompilator używał VBC. rsp.  
  
 Krótka forma `-reference` jest `/r`.  
  
## <a name="example"></a>Przykład  
 Następujące polecenie kompiluje plik źródłowy `Input.vb` i zestawy odwołań z `Metad1.dll` i `Metad2.dll` do utworzenia `Out.exe`.  
  
```console
vbc -reference:metad1.dll,metad2.dll -out:out.exe input.vb  
```  
  
## <a name="see-also"></a>Zobacz także

- [Kompilator wiersza polecenia Visual Basic](../../../visual-basic/reference/command-line-compiler/index.md)
- [-noconfig](../../../visual-basic/reference/command-line-compiler/noconfig.md)
- [-Target (Visual Basic)](../../../visual-basic/reference/command-line-compiler/target.md)
- [Public](../../../visual-basic/language-reference/modifiers/public.md)
- [Przykłady kompilacji — wiersze poleceń](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)

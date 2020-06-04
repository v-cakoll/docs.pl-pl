---
title: -reference
ms.date: 03/13/2018
helpviewer_keywords:
- /reference compiler option [Visual Basic]
- r compiler option [Visual Basic]
- -reference compiler option [Visual Basic]
- /r compiler option [Visual Basic]
- reference compiler option [Visual Basic]
- -r compiler option [Visual Basic]
ms.assetid: 66bdfced-bbf6-43d1-a554-bc0990315737
ms.openlocfilehash: 633b457106203e213f5d30003e576b7e8132f4d2
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/04/2020
ms.locfileid: "84400490"
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
 Importowane pliki muszą zawierać metadane zestawu. Tylko typy publiczne są widoczne poza zestawem. Opcja [-addmodule](addmodule.md) Importuje metadane z modułu.  
  
 Jeśli odwołujesz się do zestawu (zestawu A), który sam odwołuje się do innego zestawu (zestawu B), należy odwołać się do zestawu B, jeśli:  
  
- Typ z zestawu A dziedziczy po typie lub implementuje interfejs z zestawu B.  
  
- Wywołano pole, właściwość, zdarzenie lub metodę z typem zwracanym lub typem parametru z zestawu B.  
  
 Użyj [-LIBPATH](libpath.md) , aby określić katalog, w którym znajduje się co najmniej jedno odwołanie do zestawu.  
  
 Aby kompilator rozpoznawał typ w zestawie (nie w module), musi być zmuszony do rozpoznania typu. Przykładem tego, jak można to zrobić, jest zdefiniowanie wystąpienia typu. Inne sposoby rozpoznawania nazw typów w zestawie dla kompilatora. Na przykład, jeśli dziedziczysz z typu w zestawie, nazwa typu jest nazywana kompilatorem.  
  
 Plik odpowiedzi VBC. rsp, który odwołuje się do najczęściej używanych zestawów .NET Framework, jest używany domyślnie. Użyj, `-noconfig` Jeśli nie chcesz, aby kompilator używał VBC. rsp.  
  
 Krótka forma `-reference` to `-r` .  
  
## <a name="example"></a>Przykład  
 Poniższe polecenie kompiluje plik źródłowy `Input.vb` i zestawy odwołań z `Metad1.dll` i `Metad2.dll` do produkcji `Out.exe` .  
  
```console
vbc -reference:metad1.dll,metad2.dll -out:out.exe input.vb  
```  
  
## <a name="see-also"></a>Zobacz też

- [Kompilator wiersza polecenia Visual Basic](index.md)
- [-noconfig](noconfig.md)
- [-Target (Visual Basic)](target.md)
- [Społeczeństwo](../../language-reference/modifiers/public.md)
- [Przykłady kompilacji — wiersze poleceń](sample-compilation-command-lines.md)

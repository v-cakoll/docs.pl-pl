---
title: -optioninfer
ms.date: 07/20/2015
f1_keywords:
- -optioninfer
helpviewer_keywords:
- -optioninfer compiler option [Visual Basic]
- /optioninfer compiler option [Visual Basic]
- optioninfer compiler option [Visual Basic]
ms.assetid: f6c09db1-0553-464a-abe3-d4510c61d6ed
ms.openlocfilehash: 524660fca7c56fa490cc85169898bf2bf6d1a16e
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/04/2020
ms.locfileid: "84400581"
---
# <a name="-optioninfer"></a>-optioninfer
Umożliwia korzystanie z wnioskowania o typie lokalnym w deklaracjach zmiennych.  
  
## <a name="syntax"></a>Składnia  
  
```console  
-optioninfer[+ | -]  
```  
  
## <a name="arguments"></a>Argumenty  
  
|Termin|Definicja|  
|---|---|  
|`+`&#124;`-`|Opcjonalny. Określ `-optioninfer+` , aby włączyć wnioskowanie o typie lokalnym lub `-optioninfer-` je zablokować. `-optioninfer`Opcja bez określonej wartości jest taka sama jak `-optioninfer+` . Wartość domyślna, gdy `-optioninfer` przełącznik nie jest obecny, jest również `-optioninfer+` . Wartość domyślna jest ustawiana w pliku odpowiedzi VBC. rsp.|  
  
> [!NOTE]
> Można użyć opcji, `-noconfig` Aby zachować wewnętrzne wartości domyślne kompilatora zamiast opcji określonych w vbc. rsp. Wartość domyślna kompilatora dla tej opcji to `-optioninfer-` .  
  
## <a name="remarks"></a>Uwagi  
 Jeśli plik kodu źródłowego zawiera [instrukcję opcji wnioskowania](../../language-reference/statements/option-infer-statement.md), instrukcja zastępuje `-optioninfer` ustawienie kompilatora wiersza polecenia.  
  
### <a name="to-set--optioninfer-in-the-visual-studio-ide"></a>Aby ustawić-optioninfer w środowisku IDE programu Visual Studio  
  
1. Wybierz projekt w **Eksplorator rozwiązań**. W menu **projekt** kliknij polecenie **Właściwości**.  
  
2. Na karcie **kompilacja** Zmień wartość w polu **wnioskowanie o opcji** .  
  
## <a name="example"></a>Przykład  
 Poniższy kod kompiluje `test.vb` z włączonym wnioskem o typie lokalnym.  
  
```console
vbc -optioninfer+ test.vb  
```  
  
## <a name="see-also"></a>Zobacz też

- [Kompilator wiersza polecenia Visual Basic](index.md)
- [-optioncompare](optioncompare.md)
- [-optionexplicit](optionexplicit.md)
- [-optionstrict](optionstrict.md)
- [Przykłady kompilacji — wiersze poleceń](sample-compilation-command-lines.md)
- [Option Infer — Instrukcja](../../language-reference/statements/option-infer-statement.md)
- [Wnioskowanie o typie lokalnym](../../programming-guide/language-features/variables/local-type-inference.md)
- [Domyślne ustawienia programu Visual Basic, Projekty, Opcje — okno dialogowe](/visualstudio/ide/reference/visual-basic-defaults-projects-options-dialog-box)
- [Strona kompilowania, Projektant projektu (Visual Basic)](/visualstudio/ide/reference/compile-page-project-designer-visual-basic)
- [-noconfig](noconfig.md)
- [Tworzenie z wiersza polecenia](building-from-the-command-line.md)

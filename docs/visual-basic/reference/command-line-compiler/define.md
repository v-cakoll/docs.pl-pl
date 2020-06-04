---
title: -define
ms.date: 03/10/2018
helpviewer_keywords:
- -d compiler option [Visual Basic]
- /d compiler option [Visual Basic]
- -define compiler option [Visual Basic]
- d compiler option [Visual Basic]
- /define compiler option [Visual Basic]
- define compiler option [Visual Basic]
ms.assetid: f735c57d-1cf9-4f2f-a26f-0de630fd4077
ms.openlocfilehash: d0d1b03d9ab98f28a0112198f1ecc1e928d6d4a7
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/04/2020
ms.locfileid: "84408715"
---
# <a name="-define-visual-basic"></a>-Definiuj (Visual Basic)
Definiuje warunkowe stałe kompilatora.  
  
## <a name="syntax"></a>Składnia  
  
```console  
-define:["]symbol[=value][,symbol[=value]]["]  
```

lub

```console  
-d:["]symbol[=value][,symbol[=value]]["]  
```  
  
## <a name="arguments"></a>Argumenty  
  
|Termin|Definicja|  
|---|---|  
|`symbol`|Wymagany. Symbol do zdefiniowania.|  
|`value`|Opcjonalny. Wartość do przypisania `symbol` . Jeśli `value` jest ciągiem, musi być ujęty w nawiasy odwrotne/sekwencje znaku cudzysłowu ( \\ ") zamiast znaków cudzysłowu. Jeśli żadna wartość nie zostanie określona, jest ona prawdziwa.|  
  
## <a name="remarks"></a>Uwagi  
 `-define`Opcja ma podobny efekt jak użycie `#Const` dyrektywy preprocesora w pliku źródłowym, z tą różnicą, że stałe zdefiniowane z `-define` są publiczne i stosowane do wszystkich plików w projekcie.  
  
 Możesz użyć symboli utworzonych przez tę opcję z `#If` ... `Then` ...`#Else` dyrektywa w celu warunkowego kompilowania plików źródłowych.  
  
 `-d`jest krótką formą `-define` .  
  
 Można zdefiniować wiele symboli za pomocą `-define` przecinka do oddzielania definicji symboli.  
  
|Aby ustawić — Zdefiniuj w zintegrowanym środowisku programistycznym programu Visual Studio|  
|---|  
|1. zaznaczono projekt w **Eksplorator rozwiązań**. W menu **projekt** kliknij polecenie **Właściwości**. <br />2. Kliknij kartę **kompilacja** .<br />3. kliknij pozycję **Zaawansowane**.<br />4. Zmodyfikuj wartość w polu **stałe niestandardowe** .|  
  
## <a name="example"></a>Przykład  
 Poniższy kod definiuje, a następnie używa dwóch warunkowych stałych kompilatora.  
  
 [!code-vb[VbVbalrCompiler#45](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrCompiler/VB/Class1.vb#45)]  
  
## <a name="see-also"></a>Zobacz też

- [Kompilator wiersza polecenia Visual Basic](index.md)
- [#If... Then... #Else — dyrektywy](../../language-reference/directives/if-then-else-directives.md)
- [#Const — dyrektywa](../../language-reference/directives/const-directive.md)
- [Przykłady kompilacji — wiersze poleceń](sample-compilation-command-lines.md)

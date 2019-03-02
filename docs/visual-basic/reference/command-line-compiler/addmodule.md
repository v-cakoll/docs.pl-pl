---
title: -addmodule —
ms.date: 03/09/2018
helpviewer_keywords:
- /addmodule compiler option [Visual Basic]
- addmodule compiler option [Visual Basic]
- -addmodule compiler option [Visual Basic]
ms.assetid: fb4b89d4-4926-4f20-868d-427fa28497b2
ms.openlocfilehash: 5a6d367f4b09de600bb744aa2abed0da2c93aa0b
ms.sourcegitcommit: 41c0637e894fbcd0713d46d6ef1866f08dc321a2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/01/2019
ms.locfileid: "57202369"
---
# <a name="-addmodule"></a>-addmodule —
Powoduje, że kompilator udostępnia wszystkie informacje z określonego pliku lub plików dostępnych do aktualnie kompilowanemu projektowi typu.  
  
## <a name="syntax"></a>Składnia  
  
```  
-addmodule:fileList  
```  
  
## <a name="arguments"></a>Argumenty  
 `fileList`  
 Wymagana. Rozdzielana przecinkami lista plików, które zawierają metadanych, ale nie zawierają zestawu manifestów. Nazwy plików zawierające spacje powinny być ujęte w znaki cudzysłowu ("").  
  
## <a name="remarks"></a>Uwagi  
 Pliki według `fileList` parametr musi zostać utworzona z `-target:module` opcji lub innego kompilatora równoważna `-target:module`.  
  
 Wszystkie moduły dodawane z `-addmodule` musi znajdować się w tym samym katalogu co plik wyjściowy w czasie wykonywania. Oznacza to, że można określić modułu w dowolnym katalogu, w czasie kompilacji, ale moduł musi znajdować się w katalogu aplikacji w czasie wykonywania. Jeśli tak nie jest, możesz uzyskać <xref:System.TypeLoadException> błędu.  
  
 Jeśli określisz (jawnie lub niejawnie) wszelkie[-target (Visual Basic)](../../../visual-basic/reference/command-line-compiler/target.md) opcji innych niż `-target:module` z `-addmodule`, pliki są przekazywane do `-addmodule` stają się częścią zestawu projektu. Zestaw jest wymagany do uruchomienia pliku wyjściowego, który ma jeden lub więcej plików dodane przy użyciu `-addmodule`.  
  
 Użyj [/Reference (Visual Basic)](../../../visual-basic/reference/command-line-compiler/reference.md) można zaimportować metadanych z pliku, który zawiera zestaw.  
  
> [!NOTE]
>  `-addmodule` Opcja nie jest dostępne w środowisku programowania Visual Studio; jest dostępna tylko podczas kompilowania kodu w wierszu polecenia.  
  
## <a name="example"></a>Przykład  
 Poniższy kod tworzy moduł.  
  
 [!code-vb[VbVbalrCompiler#47](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrCompiler/VB/OptionStrictOff.vb#47)]  
  
 Poniższy kod importuje typów modułów.  
  
 [!code-vb[VbVbalrCompiler#48](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrCompiler/VB/OptionStrictOff.vb#48)]  
  
 Po uruchomieniu `t1`, wyświetla `802`.  
  
## <a name="see-also"></a>Zobacz także
- [Kompilator wiersza polecenia programu Visual Basic](../../../visual-basic/reference/command-line-compiler/index.md)
- [-target (Visual Basic)](../../../visual-basic/reference/command-line-compiler/target.md)
- [— Odwołanie (Visual Basic)](../../../visual-basic/reference/command-line-compiler/reference.md)
- [Przykłady kompilacji — wiersze poleceń](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)

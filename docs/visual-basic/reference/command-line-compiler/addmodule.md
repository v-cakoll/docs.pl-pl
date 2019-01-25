---
title: -addmodule —
ms.date: 03/09/2018
helpviewer_keywords:
- /addmodule compiler option [Visual Basic]
- addmodule compiler option [Visual Basic]
- -addmodule compiler option [Visual Basic]
ms.assetid: fb4b89d4-4926-4f20-868d-427fa28497b2
ms.openlocfilehash: 3e5c94cce8b16649854050855800ac1bf2fc6572
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54580580"
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
  
 [!code-vb[VbVbalrCompiler#47](../../../visual-basic/reference/command-line-compiler/codesnippet/VisualBasic/addmodule_1.vb)]  
  
 Poniższy kod importuje typów modułów.  
  
 [!code-vb[VbVbalrCompiler#48](../../../visual-basic/reference/command-line-compiler/codesnippet/VisualBasic/addmodule_2.vb)]  
  
 Po uruchomieniu `t1`, wyświetla `802`.  
  
## <a name="see-also"></a>Zobacz także
- [Kompilator wiersza polecenia programu Visual Basic](../../../visual-basic/reference/command-line-compiler/index.md)
- [-target (Visual Basic)](../../../visual-basic/reference/command-line-compiler/target.md)
- [— Odwołanie (Visual Basic)](../../../visual-basic/reference/command-line-compiler/reference.md)
- [Przykłady kompilacji — wiersze poleceń](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)

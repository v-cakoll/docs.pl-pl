---
title: -addmodule
ms.date: 03/09/2018
helpviewer_keywords:
- /addmodule compiler option [Visual Basic]
- addmodule compiler option [Visual Basic]
- -addmodule compiler option [Visual Basic]
ms.assetid: fb4b89d4-4926-4f20-868d-427fa28497b2
ms.openlocfilehash: dd98b45d75ff421dc81666ed47695132a49bfa3a
ms.sourcegitcommit: 4f4a32a5c16a75724920fa9627c59985c41e173c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/17/2019
ms.locfileid: "72524480"
---
# <a name="-addmodule"></a>-addmodule
Powoduje, że kompilator udostępnił wszystkie informacje o typie z określonych plików dla aktualnie kompilowanego projektu.  
  
## <a name="syntax"></a>Składnia  
  
```console  
-addmodule:fileList  
```  
  
## <a name="arguments"></a>Argumenty  
 `fileList`  
 Wymagany. Rozdzielana przecinkami lista plików, które zawierają metadane, ale nie zawierają manifestów zestawów. Nazwy plików zawierające spacje powinny być ujęte w znaki cudzysłowu ("").  
  
## <a name="remarks"></a>Uwagi  
 Pliki wymienione przez `fileList` parametr muszą zostać utworzone przy użyciu `-target:module` opcji lub innego kompilatora, który `-target:module`jest odpowiednikiem.  
  
 Wszystkie dodane moduły `-addmodule` muszą znajdować się w tym samym katalogu, co plik wyjściowy w czasie wykonywania. Oznacza to, że można określić moduł w dowolnym katalogu w czasie kompilacji, ale moduł musi znajdować się w katalogu aplikacji w czasie wykonywania. Jeśli tak nie jest, zostanie wyświetlony <xref:System.TypeLoadException> komunikat o błędzie.  
  
 Jeśli określisz (niejawnie lub jawnie) opcję[docelową (Visual Basic)](../../../visual-basic/reference/command-line-compiler/target.md) inną `-target:module` niż `-addmodule`with, pliki przekazywane do `-addmodule` zestawu projektu stają się częścią. Zestaw jest wymagany do uruchomienia pliku wyjściowego, który ma co najmniej jeden plik, który został `-addmodule`dodany za pomocą.  
  
 Użyj [parametru-reference (Visual Basic)](../../../visual-basic/reference/command-line-compiler/reference.md) do zaimportowania metadanych z pliku, który zawiera zestaw.  
  
> [!NOTE]
> `-addmodule` Opcja jest niedostępna w środowisku deweloperskim programu Visual Studio; jest on dostępny tylko w przypadku kompilowania z wiersza polecenia.  
  
## <a name="example"></a>Przykład  
 Poniższy kod tworzy moduł.  
  
 [!code-vb[VbVbalrCompiler#47](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrCompiler/VB/OptionStrictOff.vb#47)]  
  
 Poniższy kod importuje typy modułu.  
  
 [!code-vb[VbVbalrCompiler#48](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrCompiler/VB/OptionStrictOff.vb#48)]  
  
 Po uruchomieniu `t1`programu jest to wyjście `802`.  
  
## <a name="see-also"></a>Zobacz też

- [Kompilator wiersza polecenia Visual Basic](../../../visual-basic/reference/command-line-compiler/index.md)
- [-Target (Visual Basic)](../../../visual-basic/reference/command-line-compiler/target.md)
- [-Reference (Visual Basic)](../../../visual-basic/reference/command-line-compiler/reference.md)
- [Przykłady kompilacji — wiersze poleceń](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)

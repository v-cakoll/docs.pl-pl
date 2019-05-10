---
title: With...End With — Instrukcja (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vb.With
helpviewer_keywords:
- With keyword [Visual Basic]
- loop structures [Visual Basic], and With...End With statements
- execution [Visual Basic], on object
- instructions, repeating
- With...End With statements [Visual Basic]
- With statement [Visual Basic]
- With statement [Visual Basic], nesting
- objects [Visual Basic], accessing
- With block
- End keyword [Visual Basic], With...End With statements
ms.assetid: 340d5fbb-4f43-48ec-a024-80843c137817
ms.openlocfilehash: 38a34a4662d969fd526963744b8bd493952d9cff
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/28/2019
ms.locfileid: "64615071"
---
# <a name="withend-with-statement-visual-basic"></a>With...End With — Instrukcja (Visual Basic)
Wykonuje szereg instrukcji, które wielokrotnie odwołują się do pojedynczego obiektu lub struktury, dzięki czemu instrukcje mogą używać uproszczonej składni podczas uzyskiwania dostępu do członków obiektu lub struktury.  Korzystając ze struktury możesz jedynie odczytać wartości członków lub wywoływać metody i wystąpi błąd, jeśli zostanie podjęta próba przypisania wartości do członków struktury używanych w `With...End With` instrukcji.  
  
## <a name="syntax"></a>Składnia  
  
```  
With objectExpression  
    [ statements ]  
End With  
```  
  
## <a name="parts"></a>Części  
  
|Termin|Definicja|  
|---|---|  
|`objectExpression`|Wymagana. Wyrażenie, które zostaje oszacowane do obiektu. Wyrażenie może być dowolnie złożone i jest sprawdzane tylko raz. Wyrażenie może być dowolnego typu danych, w tym typów podstawowych.|  
|`statements`|Opcjonalna. Jedna lub więcej instrukcji między `With` i `End With` które mogą się odwoływać do członków obiektu, który jest wytwarzany przez ocenę `objectExpression`.|  
|`End With`|Wymagana. Kończy definicję `With` bloku.|  
  
## <a name="remarks"></a>Uwagi  
 Za pomocą `With...End With`, można wykonać serię instrukcji na określonym obiekcie bez określania nazwy obiektu wiele razy. W ramach `With` blok instrukcji, można określić członka obiektu, rozpoczynając od kropki, tak jakby `With` obiektu instrukcji go poprzedzał.  
  
 Na przykład, aby zmienić wiele właściwości dla pojedynczego obiektu, umieść instrukcje przypisania właściwości wewnątrz `With...End With` bloku, odwołanie do obiektu tylko raz zamiast raz dla każdego przypisania właściwości.  
  
 Jeśli kod uzyskuje dostęp do tego samego obiektu w wielu instrukcjach, uzyskasz następujące korzyści za pomocą `With` instrukcji:  
  
- Nie musisz szacować złożonego wyrażenia wiele razy ani przypisywać wyniku do zmiennej tymczasowej, aby odwołać się do jego członków wiele razy.  
  
- Kod staje się bardziej czytelny dzięki eliminacji powtarzających się wyrażeń kwalifikujących.  
  
 Typ danych `objectExpression` może być dowolną klasę lub typ struktury lub nawet typ podstawowy języka Visual Basic taką jak `Integer`.  Jeśli `objectExpression` wyniki coś innego niż obiekt można tylko odczytać wartości jego członków lub wywoływać metody i wystąpi błąd, jeśli zostanie podjęta próba przypisania wartości do członków struktury używanych w `With...End With` instrukcji.  Jest to ten sam błąd, jeśli wywołano metodę, która zwróciła strukturę i natychmiast uzyskać dostęp i przypisać wartość do członka wyniku funkcji, takich jak `GetAPoint().x = 1`.  Problem w obu przypadkach jest taki, że struktura istnieje tylko na stosie wywołań i nie ma żadnego sposobu, aby członek zmodyfikowanej struktury w takich sytuacjach mógł pisać do takich lokalizacji, żeby inny kod w programie mógł obserwować zmiany.  
  
 `objectExpression` Jest wykonywane tylko raz, po wejściu do bloku. Nie można ponownie przypisać `objectExpression` z poziomu `With` bloku.  
  
 W ramach `With` bloku, jest dostępne metody i właściwości jedynie określonego obiektu bez ich kwalifikowania. Możesz użyć metod i właściwości innych obiektów, ale musisz je zakwalifikować z ich nazwami obiektów.  
  
 Możesz umieścić jedną `With...End With` instrukcji w innym. Zagnieżdżone `With...End With` instrukcji może być skomplikowane, jeśli obiekty, które są określone, nie są jasne z kontekstu. Należy podać w pełni kwalifikowane odwołanie do obiektu, który znajduje się w zewnętrznym `With` zablokować, jeśli odwołanie do obiektu pochodzi z wewnętrznego `With` bloku.  
  
 Nie można rozgałęzić do `With` bloku instrukcji poza blokiem.  
  
 Instrukcje są wykonywane tylko raz, chyba że blok zawiera pętlę. Możesz zagnieździć różne rodzaje struktur sterujących. Aby uzyskać więcej informacji, zobacz [zagnieżdżone struktury sterujące](../../../visual-basic/programming-guide/language-features/control-flow/nested-control-structures.md).  
  
> [!NOTE]
>  Możesz użyć `With` również słowa kluczowego w inicjatorach obiektów. Aby uzyskać więcej informacji i przykładów, zobacz [inicjatory obiektów: Typy nazwane i anonimowe](../../../visual-basic/programming-guide/language-features/objects-and-classes/object-initializers-named-and-anonymous-types.md) i [typy anonimowe](../../../visual-basic/programming-guide/language-features/objects-and-classes/anonymous-types.md).  
>   
>  Jeśli używasz `With` bloku tylko do zainicjowania właściwości lub pól obiektu, który został właśnie utworzony, rozważ użycie zamiast tego inicjatora obiektu.  
  
## <a name="example"></a>Przykład  
 W poniższym przykładzie każdy `With` bloku wykonuje serię instrukcji na pojedynczym obiekcie.  
  
 [!code-vb[VbVbalrWithStatement#2](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/vbvbalrwithstatement/vb/mainwindow.xaml.vb#2)]  
  
## <a name="example"></a>Przykład  
 Poniższy przykład zagnieżdża instrukcje `With…End With` instrukcji. W ramach zagnieżdżonej `With` instrukcji, składnia odnosi się do obiektu wewnętrznego.  
  
 [!code-vb[VbVbalrWithStatement#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/vbvbalrwithstatement/vb/mainwindow.xaml.vb#1)]  
  
## <a name="see-also"></a>Zobacz także

- <xref:System.Collections.Generic.List%601>
- [Zagnieżdżone struktury sterujące](../../../visual-basic/programming-guide/language-features/control-flow/nested-control-structures.md)
- [Inicjatory obiektów: Typy nazwane i anonimowe](../../../visual-basic/programming-guide/language-features/objects-and-classes/object-initializers-named-and-anonymous-types.md)
- [Typy anonimowe](../../../visual-basic/programming-guide/language-features/objects-and-classes/anonymous-types.md)

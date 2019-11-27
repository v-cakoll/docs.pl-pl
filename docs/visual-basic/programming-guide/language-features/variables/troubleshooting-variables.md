---
title: Rozwiązywanie problemów związanych ze zmiennymi
ms.date: 07/20/2015
helpviewer_keywords:
- troubleshooting [Visual Basic], variables
- variables [Visual Basic], troubleshooting
ms.assetid: 928a2dc8-e565-4ae4-8ba3-80cc0cb50090
ms.openlocfilehash: 929540788e8134760446e02c3377e78d00ca17d9
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/22/2019
ms.locfileid: "74351775"
---
# <a name="troubleshooting-variables-in-visual-basic"></a>Rozwiązywanie problemów związanych ze zmiennymi w Visual Basic
Ta strona zawiera listę typowych problemów, które mogą wystąpić podczas pracy ze zmiennymi w Visual Basic.  
  
## <a name="unable-to-access-members-of-an-object"></a>Nie można uzyskać dostępu do elementów członkowskich obiektu  
 Jeśli kod próbuje uzyskać dostęp do właściwości lub metody obiektu, istnieją dwa możliwe przyczyny błędu:  
  
- Kompilator może generować komunikat o błędzie, Jeśli deklarujesz zmienną obiektu jako określony typ, a następnie odwołujesz się do elementu członkowskiego, który nie jest zdefiniowany przez ten typ.  
  
- <xref:System.MemberAccessException> w czasie wykonywania występuje, gdy obiekt przypisany do zmiennej obiektu nie ujawnia elementu członkowskiego, do którego kod próbuje uzyskać dostęp. W przypadku zmiennej [typu danych obiektu](../../../../visual-basic/language-reference/data-types/object-data-type.md)można także uzyskać ten wyjątek, jeśli element członkowski nie jest `Public`. Jest to spowodowane tym, że późne wiązanie zezwala na dostęp tylko do `Public` elementów członkowskich.  
  
 Gdy [instrukcja Option Strict](../../../../visual-basic/language-reference/statements/option-strict-statement.md) ustawia typ `On`, zmienna obiektu może uzyskać dostęp tylko do metod i właściwości klasy, z którą ją deklarujesz. Ilustruje to poniższy przykład.  

 [!code-vb[VbVbalrVariables#2](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrVariables/VB/Class1.vb#2)]  
  
 W tym przykładzie `p` mogą korzystać tylko z elementów członkowskich klasy <xref:System.Object>, które nie zawierają właściwości `Left`. Z drugiej strony, `q` został zadeklarowany jako typu <xref:System.Windows.Forms.Label>, dlatego można użyć wszystkich metod i właściwości klasy <xref:System.Windows.Forms.Label> w przestrzeni nazw <xref:System.Windows.Forms>.  
  
### <a name="correct-approach"></a>Poprawne podejście  
 Aby można było uzyskać dostęp do wszystkich elementów członkowskich obiektu określonej klasy, należy zadeklarować zmienną obiektu jako typ tej klasy, gdy jest to możliwe. Jeśli nie możesz tego zrobić, na przykład jeśli nie znasz typu obiektu w czasie kompilacji, musisz ustawić `Option Strict` na `Off` i zadeklarować zmienną jako [Typ danych obiektu](../../../../visual-basic/language-reference/data-types/object-data-type.md). Pozwala to na przypisanie obiektów dowolnego typu do zmiennej i należy wykonać kroki, aby upewnić się, że aktualnie przypisany obiekt ma akceptowalny typ. Można użyć [operatora typeof](../../../../visual-basic/language-reference/operators/typeof-operator.md) , aby dokonać tego ustalenia.  
  
## <a name="other-components-cannot-access-your-variable"></a>Inne składniki nie mogą uzyskać dostępu do zmiennej  
 Nazwy Visual Basic nie uwzględniają *wielkości liter*. Jeśli dwie nazwy różnią się tylko wielkością liter, kompilator interpretuje je jako tę samą nazwę. Na przykład uważa, że `ABC` i `abc` do odwoływania się do tego samego zadeklarowanego elementu.  
  
 Jednak środowisko uruchomieniowe języka wspólnego (CLR) używa powiązania *z rozróżnianiem wielkości liter* . W związku z tym, podczas tworzenia zestawu lub biblioteki DLL i udostępnienia go innym zestawom nazwy nie są dłuższe. Na przykład, jeśli zdefiniujesz klasę z elementem o nazwie `ABC`, a inne zestawy używają klasy przez środowisko uruchomieniowe języka wspólnego, muszą odwoływać się do elementu jako `ABC`. Jeśli następnie ponownie skompilujesz klasę i zmienisz nazwę elementu na `abc`, inne zestawy korzystające z klasy nie będą miały już dostępu do tego elementu. W związku z tym po wydaniu zaktualizowanej wersji zestawu nie należy zmieniać wielkości liter każdego z elementów publicznych.  
  
 Aby uzyskać więcej informacji, zobacz [środowisko uruchomieniowe języka wspólnego](../../../../standard/clr.md).  
  
### <a name="correct-approach"></a>Poprawne podejście  
 Aby zezwolić innym składnikom na dostęp do zmiennych, Traktuj ich nazwy tak, jakby były rozróżniane wielkości liter. Podczas testowania klasy lub modułu upewnij się, że inne zestawy są powiązane ze zmiennymi, których oczekujesz. Po opublikowaniu składnika nie należy wprowadzać żadnych modyfikacji istniejących nazw zmiennych, w tym zmiany ich przypadków.  
  
## <a name="wrong-variable-being-used"></a>Nieprawidłowa zmienna jest używana  
 Jeśli masz więcej niż jedną zmienną o tej samej nazwie, kompilator Visual Basic próbuje rozpoznać każde odwołanie do tej nazwy. Jeśli zmienne mają różne zakresy, kompilator rozpoznaje odwołanie do deklaracji z najwęższym zakresem. Jeśli mają ten sam zakres, rozpoznawanie kończy się niepowodzeniem, a kompilator sygnalizuje błąd. Aby uzyskać więcej informacji, zobacz [odwołania do zadeklarowanych elementów](../../../../visual-basic/programming-guide/language-features/declared-elements/references-to-declared-elements.md).  
  
### <a name="correct-approach"></a>Poprawne podejście  
 Należy unikać używania zmiennych o takiej samej nazwie, ale innym zakresie. Jeśli używasz innych zestawów lub projektów, Unikaj używania nazw zdefiniowanych w tych składnikach zewnętrznych tak długo, jak to możliwe. Jeśli masz więcej niż jedną zmienną o tej samej nazwie, pamiętaj, aby zakwalifikować się do niej każde odwołanie. Aby uzyskać więcej informacji, zobacz [odwołania do zadeklarowanych elementów](../../../../visual-basic/programming-guide/language-features/declared-elements/references-to-declared-elements.md).  
  
## <a name="see-also"></a>Zobacz także

- [Zmienne](../../../../visual-basic/programming-guide/language-features/variables/index.md)
- [Deklaracja zmiennej](../../../../visual-basic/programming-guide/language-features/variables/variable-declaration.md)
- [Zmienne obiektów](../../../../visual-basic/programming-guide/language-features/variables/object-variables.md)
- [Deklaracja zmiennej obiektu](../../../../visual-basic/programming-guide/language-features/variables/object-variable-declaration.md)
- [Instrukcje: dostęp do elementów członkowskich obiektu](../../../../visual-basic/programming-guide/language-features/variables/how-to-access-members-of-an-object.md)
- [Wartości zmiennej obiektu](../../../../visual-basic/programming-guide/language-features/variables/object-variable-values.md)
- [Instrukcje: określanie, do jakiego typu odnosi się zmienna obiektu](../../../../visual-basic/programming-guide/language-features/variables/how-to-determine-what-type-an-object-variable-refers-to.md)
- [Odwołania do elementów zadeklarowanych](../../../../visual-basic/programming-guide/language-features/declared-elements/references-to-declared-elements.md)
- [Nazwy zadeklarowanych elementów](../../../../visual-basic/programming-guide/language-features/declared-elements/declared-element-names.md)

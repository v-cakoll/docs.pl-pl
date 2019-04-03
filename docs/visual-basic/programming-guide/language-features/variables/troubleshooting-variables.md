---
title: Rozwiązywanie problemów związanych ze zmiennymi w Visual Basic
ms.date: 07/20/2015
helpviewer_keywords:
- troubleshooting [Visual Basic], variables
- variables [Visual Basic], troubleshooting
ms.assetid: 928a2dc8-e565-4ae4-8ba3-80cc0cb50090
ms.openlocfilehash: 55d0fdcdbed4f994e50e83e5a25baf83c3ad79cc
ms.sourcegitcommit: bce0586f0cccaae6d6cbd625d5a7b824d1d3de4b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/02/2019
ms.locfileid: "58831127"
---
# <a name="troubleshooting-variables-in-visual-basic"></a>Rozwiązywanie problemów związanych ze zmiennymi w Visual Basic
Ta strona zawiera listę niektórych typowych problemów, które mogą wystąpić podczas pracy ze zmiennymi w Visual Basic.  
  
## <a name="unable-to-access-members-of-an-object"></a>Nie można dostępu do elementów członkowskich obiektu  
 Jeśli kod próbuje uzyskać dostęp do właściwości lub metody na obiekt, istnieją dwie sytuacje możliwy błąd:  
  
-   Kompilator może wygenerować komunikat o błędzie, jeśli zadeklarujesz zmienną obiektu określonego typu i następnie odwoływać się do elementu członkowskiego nie jest zdefiniowany przez tego typu.  
  
-   Środowiska wykonawczego <xref:System.MemberAccessException> występuje, gdy obiekt, który został przypisany do zmiennej obiektu nie ujawnia kod próbuje uzyskać dostęp do elementu członkowskiego. W przypadku zmiennej [Object — typ danych](../../../../visual-basic/language-reference/data-types/object-data-type.md), można również uzyskać ten wyjątek, jeśli element członkowski nie jest `Public`. Jest to spowodowane późnym wiązaniu zezwala na dostęp tylko do `Public` elementów członkowskich.  
  
 Gdy [Option Strict — instrukcja](../../../../visual-basic/language-reference/statements/option-strict-statement.md) kontrola typów zestawów `On`, zmienna obiektu dostęp do metod i właściwości klasy, z którym trzeba je zadeklarować. Ilustruje to poniższy przykład.  

 [!code-vb[VbVbalrVariables#2](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrVariables/VB/Class1.vb#2)]  
  
 W tym przykładzie `p` można używać tylko członków <xref:System.Object> klasy, które nie obejmują `Left` właściwości. Z drugiej strony `q` został zadeklarowany jako typ <xref:System.Windows.Forms.Label>, dzięki czemu można użyć wszystkich metod i właściwości <xref:System.Windows.Forms.Label> klasy w <xref:System.Windows.Forms> przestrzeni nazw.  
  
### <a name="correct-approach"></a>Właściwe podejście  
 Aby umożliwić dostęp do wszystkich elementów członkowskich obiekt określonej klasy, należy zadeklarować zmienną obiektu typu tej klasy, gdy jest to możliwe. Jeśli nie możesz tego zrobić, na przykład, jeśli nie znasz obiektu typu w czasie kompilacji, należy ustawić `Option Strict` do `Off` i Zadeklaruj zmienną [Object — typ danych](../../../../visual-basic/language-reference/data-types/object-data-type.md). Dzięki temu obiekty dowolnego typu ma być przypisane do zmiennej, a następnie należy wykonać czynności, aby upewnij się, że aktualnie przydzielony obiekt typu dopuszczalne. Możesz użyć [TypeOf — Operator](../../../../visual-basic/language-reference/operators/typeof-operator.md) Aby określić to.  
  
## <a name="other-components-cannot-access-your-variable"></a>Inne składniki nie może uzyskać dostępu do zmiennej  
 Nazwy języka Visual Basic są *bez uwzględniania wielkości liter*. Jeśli dwie nazwy różnią się alfabetyczne tylko wielkością liter, kompilator interpretuje je jako tej samej nazwie. Na przykład, które uzna za `ABC` i `abc` do odwoływania się do tego samego elementu zadeklarowane.  
  
 Środowisko uruchomieniowe języka wspólnego (CLR) używa *liter* powiązania. W związku z tym podczas tworzenia zestawu lub biblioteki DLL i był dostępny dla innych zestawów, nazwy nie są już bez uwzględniania wielkości liter. Na przykład, jeśli zdefiniujesz klasę z elementu o nazwie `ABC`, i innych zestawów, należy użyć klasy za pomocą środowiska uruchomieniowego języka wspólnego, ich musi odwoływać się do elementu jako `ABC`. Jeśli są później ponownie skompilować klasy i Zmień nazwę elementu do `abc`, zestawy, przy użyciu klasy mogą nie uzyskać dostępu do tego elementu. W związku z tym po zwolnieniu zaktualizowanej wersji zestawu, nie należy zmieniać wielkość liter alfabetu wszelkie publiczne elementy.  
  
 Aby uzyskać więcej informacji, zobacz [środowiska uruchomieniowego języka wspólnego](../../../../standard/clr.md).  
  
### <a name="correct-approach"></a>Właściwe podejście  
 Aby zezwolić na dostęp do zmiennych inne składniki, należy traktować ich nazw, jakby pochodziły z uwzględnieniem wielkości liter. Podczas testowania klasy lub modułu, upewnij się, że dokonywane jest wiązanie zmienne, których oczekujesz od ich do innych zestawów. Po opublikowaniu składnika, nie należy wprowadzać wszelkie zmiany w istniejącej nazwy zmiennych, łącznie ze zmianą ich przypadki.  
  
## <a name="wrong-variable-being-used"></a>Niewłaściwy zmiennej używane  
 Jeśli masz więcej niż jedną zmienną o takiej samej nazwie, kompilator Visual Basic próbuje rozpoznać każde odwołanie do tej nazwy. Jeśli zmienne mają inny zakres, kompilator rozpoznaje odwołanie do deklaracji z najwęższego zakresu. Jeśli mają tego samego zakresu, rozwiązanie nie powiedzie się i kompilator sygnalizuje błąd. Aby uzyskać więcej informacji, zobacz [Odwołania do zadeklarowanych elementów](../../../../visual-basic/programming-guide/language-features/declared-elements/references-to-declared-elements.md).  
  
### <a name="correct-approach"></a>Właściwe podejście  
 Należy unikać używania zmiennych o tej samej nazwie, ale inny zakres. Jeśli używasz innych projektów lub zestawów, należy unikać żadnych nazw zdefiniowane w tych składników zewnętrznych, jak to możliwe. Jeśli masz więcej niż jedną zmienną o takiej samej nazwie, upewnij się, że spełniasz każde odwołanie do niego. Aby uzyskać więcej informacji, zobacz [Odwołania do zadeklarowanych elementów](../../../../visual-basic/programming-guide/language-features/declared-elements/references-to-declared-elements.md).  
  
## <a name="see-also"></a>Zobacz także

- [Zmienne](../../../../visual-basic/programming-guide/language-features/variables/index.md)
- [Deklaracja zmiennej](../../../../visual-basic/programming-guide/language-features/variables/variable-declaration.md)
- [Zmienne obiektów](../../../../visual-basic/programming-guide/language-features/variables/object-variables.md)
- [Deklaracja zmiennej obiektu](../../../../visual-basic/programming-guide/language-features/variables/object-variable-declaration.md)
- [Instrukcje: Dostęp do elementów członkowskich obiektu](../../../../visual-basic/programming-guide/language-features/variables/how-to-access-members-of-an-object.md)
- [Wartości zmiennej obiektu](../../../../visual-basic/programming-guide/language-features/variables/object-variable-values.md)
- [Instrukcje: Wyznaczyć, jakiego typu odnosi się zmienna obiektu](../../../../visual-basic/programming-guide/language-features/variables/how-to-determine-what-type-an-object-variable-refers-to.md)
- [Odwołania do elementów zadeklarowanych](../../../../visual-basic/programming-guide/language-features/declared-elements/references-to-declared-elements.md)
- [Nazwy zadeklarowanych elementów](../../../../visual-basic/programming-guide/language-features/declared-elements/declared-element-names.md)

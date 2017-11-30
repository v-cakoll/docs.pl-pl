---
title: "Rozwiązywanie problemów związanych ze zmiennymi w Visual Basic"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- troubleshooting [Visual Basic], variables
- variables [Visual Basic], troubleshooting
ms.assetid: 928a2dc8-e565-4ae4-8ba3-80cc0cb50090
caps.latest.revision: "20"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: bf6d2a0c7318c12b3001a92a8aa06625b4edabb6
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="troubleshooting-variables-in-visual-basic"></a>Rozwiązywanie problemów związanych ze zmiennymi w Visual Basic
Ta strona zawiera listę typowych problemów, które mogą wystąpić podczas pracy z zmiennych w [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)].  
  
## <a name="unable-to-access-members-of-an-object"></a>Nie można dostępu do elementów członkowskich obiektu  
 Jeśli kodu próbuje uzyskać dostęp do właściwości lub metody dla obiekt, istnieją dwa wyników może zawierać błąd:  
  
-   Kompilator może wygenerować komunikat o błędzie, jeśli deklarowanie zmiennej obiektu określonego typu i następnie odwoływać się do elementu członkowskiego nie wynika z tego typu.  
  
-   Środowiska wykonawczego <xref:System.MemberAccessException> występuje, gdy obiekt przypisaną do zmiennej obiektu nie ujawnia kodu próbuje uzyskać dostęp do elementu członkowskiego. W przypadku zmiennej [Object — typ danych](../../../../visual-basic/language-reference/data-types/object-data-type.md), można także uzyskać ten wyjątek, jeśli element członkowski nie jest `Public`. Wynika to z faktu późne wiązanie zezwala na dostęp tylko do `Public` elementów członkowskich.  
  
 Gdy [Option Strict — instrukcja](../../../../visual-basic/language-reference/statements/option-strict-statement.md) kontrola typów zestawów `On`, zmienna obiektu można uzyskać dostęp tylko metody i właściwości klasy, z którym należy zadeklarować. Ilustruje to poniższy przykład.  

 [!code-vb[VbVbalrVariables#2](../../../../visual-basic/programming-guide/language-features/variables/codesnippet/VisualBasic/troubleshooting-variables_1.vb)]  
  
 W tym przykładzie `p` można używać tylko członkowie <xref:System.Object> klasy, które nie obejmują `Left` właściwości. Z drugiej strony `q` został zadeklarowany jako typ <xref:System.Windows.Forms.Label>, dlatego można używać metod i właściwości <xref:System.Windows.Forms.Label> klasy w <xref:System.Windows.Forms> przestrzeni nazw.  
  
### <a name="correct-approach"></a>Popraw podejście  
 Aby mogły uzyskiwać dostęp do wszystkich elementów członkowskich w obiekcie określonej klasy, należy zadeklarować zmienną obiektu typu tej klasy, jeśli to możliwe. Jeśli nie możesz tego zrobić, na przykład, jeśli nie znasz obiektu typu w czasie kompilacji, należy ustawić `Option Strict` do `Off` i zadeklarować zmienną za [Object — typ danych](../../../../visual-basic/language-reference/data-types/object-data-type.md). Dzięki temu obiekty dowolnego typu do przypisania do zmiennej i należy wykonać kroki, aby upewnić się, że obecnie przypisany obiekt jest typu akceptowalnego. Można użyć [TypeOf Operator](../../../../visual-basic/language-reference/operators/typeof-operator.md) Aby określić to.  
  
## <a name="other-components-cannot-access-your-variable"></a>Inne składniki nie może uzyskać dostępu do zmiennej  
 [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)]nazwy są *bez uwzględniania wielkości liter*. Jeśli dwie nazwy różnią się od litery alfabetu tylko wielkością liter, kompilator interpretuje je jako takiej samej nazwie. Na przykład traktuje `ABC` i `abc` do odwoływania się do tego samego elementu zadeklarowane.  
  
 Środowisko uruchomieniowe języka wspólnego (CLR) nie korzysta jednak *z uwzględnieniem wielkości liter* powiązania. W związku z tym podczas tworzenia zestawu lub biblioteki DLL i był dostępny do innych zestawów nazwy nie są już bez uwzględniania wielkości liter. Na przykład można zdefiniować klasę z element o nazwie `ABC`, i innych zestawów użyć klasy przez środowisko uruchomieniowe języka wspólnego, ich musi odwoływać się do elementu jako `ABC`. Jeśli są później ponownie skompilowana, klasy i Zmień nazwę elementu, aby `abc`, innych zestawów przy użyciu klasy nie może uzyskać dostępu do tego elementu. W związku z tym po zwolnieniu zaktualizowanej wersji zestawu, nie należy zmieniać w przypadku alfabetyczne żadnych publicznych elementów.  
  
 Aby uzyskać więcej informacji, zobacz [środowisko uruchomieniowe języka wspólnego](../../../../standard/clr.md).  
  
### <a name="correct-approach"></a>Popraw podejście  
 Aby zezwolić innym składnikom dostęp do zmiennych, traktować ich nazwy, tak jakby były z uwzględnieniem wielkości liter. Podczas testowania programu klasę lub moduł, upewnij się, że dokonywane jest wiązanie zmiennych, które oczekują je do innych zestawów. Po opublikowaniu składnik, nie należy wprowadzać zmiany istniejącej nazwy zmiennych, łącznie ze zmianą ich przypadków.  
  
## <a name="wrong-variable-being-used"></a>Niewłaściwy zmiennej używany  
 Jeśli masz więcej niż jedną zmienną o takiej samej nazwie [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] kompilatora próbuje rozpoznać każdego odwołania do tej nazwy. Jeśli zmienne inny zakres, kompilator usuwa odwołanie do deklaracji z najwęższy zakres. Gdy mają ten sam zakres rozpoznawania nie powiedzie się i kompilator sygnały wystąpił błąd. Aby uzyskać więcej informacji, zobacz [odwołania do elementów zadeklarowany](../../../../visual-basic/programming-guide/language-features/declared-elements/references-to-declared-elements.md).  
  
### <a name="correct-approach"></a>Popraw podejście  
 Unikaj używania zmiennych o tej samej nazwie, ale inny zakres. Jeśli korzystasz z innych zestawów lub projektów, należy unikać żadnych nazw zdefiniowana w tych składników zewnętrznych, jak to możliwe. Jeśli masz więcej niż jedną zmienną o takiej samej nazwie, upewnij się, że możesz skorzystać z każde odwołanie do niego. Aby uzyskać więcej informacji, zobacz [odwołania do elementów zadeklarowany](../../../../visual-basic/programming-guide/language-features/declared-elements/references-to-declared-elements.md).  
  
## <a name="see-also"></a>Zobacz też  
 [Zmienne](../../../../visual-basic/programming-guide/language-features/variables/index.md)  
 [Deklaracja zmiennej](../../../../visual-basic/programming-guide/language-features/variables/variable-declaration.md)  
 [Zmienne obiektów](../../../../visual-basic/programming-guide/language-features/variables/object-variables.md)  
 [Deklaracja zmiennej obiektu](../../../../visual-basic/programming-guide/language-features/variables/object-variable-declaration.md)  
 [Porady: dostęp do elementów członkowskich obiektu](../../../../visual-basic/programming-guide/language-features/variables/how-to-access-members-of-an-object.md)  
 [Wartości zmiennej obiektu](../../../../visual-basic/programming-guide/language-features/variables/object-variable-values.md)  
 [Porady: wyznaczyć, jakiego typu odnosi się zmienna obiektu](../../../../visual-basic/programming-guide/language-features/variables/how-to-determine-what-type-an-object-variable-refers-to.md)  
 [Odwołania do elementów zadeklarowanych](../../../../visual-basic/programming-guide/language-features/declared-elements/references-to-declared-elements.md)  
 [Zadeklarowane nazwy elementów](../../../../visual-basic/programming-guide/language-features/declared-elements/declared-element-names.md)

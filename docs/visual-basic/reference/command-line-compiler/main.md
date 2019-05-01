---
title: -main
ms.date: 03/13/2018
helpviewer_keywords:
- main compiler option [Visual Basic]
- /main compiler option [Visual Basic]
- -main compiler option [Visual Basic]
ms.assetid: 83fc339d-6652-415d-b205-b5133319b5b0
ms.openlocfilehash: fd6240faf702ccb5e543bfd6a7779284f38d8850
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61793916"
---
# <a name="-main"></a>-main
Określa klasę lub moduł, który zawiera `Sub Main` procedury.  
  
## <a name="syntax"></a>Składnia  
  
```  
-main:location  
```  
  
## <a name="arguments"></a>Argumenty  
 `location`  
 Wymagana. Nazwa klasy lub moduł, który zawiera `Sub Main` procedury wywoływanej po uruchomieniu programu. Może to być w formie **-main: moduł** lub **-main:namespace.module**.  
  
## <a name="remarks"></a>Uwagi  
 Użyj tej opcji, podczas tworzenia pliku wykonywalnego lub program wykonywalny Windows. Jeśli **-głównego** zostanie pominięta opcja, kompilator szuka prawidłową udostępnione `Sub Main` we wszystkich publiczne klasy i moduły.  
  
 Zobacz [procedura Main w języku Visual Basic](../../../visual-basic/programming-guide/program-structure/main-procedure.md) dyskusję na temat różnych metod `Main` procedury.  
  
 Gdy `location` to klasa, która dziedziczy po elemencie <xref:System.Windows.Forms.Form>, kompilator udostępnia domyślny `Main` procedury, która uruchamia aplikację, jeśli nie ma klasy `Main` procedury. Dzięki temu można skompilować kod w wierszu polecenia, który został utworzony w środowisku programistycznym.  
  
 [!code-vb[VbVbalrCompiler#16](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrCompiler/VB/Class1.vb#16)]  
  
### <a name="to-set--main-in-the-visual-studio-integrated-development-environment"></a>Aby ustawić — główny w programie Visual Studio zintegrowanego środowiska programistycznego  
  
1. Projekt wybrany w **Eksploratora rozwiązań**. Na **projektu** menu, kliknij przycisk **właściwości**.  
  
2. Kliknij przycisk **aplikacji** kartę.  
  
3. Upewnij się, że **struktury aplikacji Włącz** nie zaznaczono pola wyboru.  
  
4. Zmodyfikuj wartość w **obiekt początkowy** pole.  
  
## <a name="example"></a>Przykład  
 Poniższy kod kompiluje `T2.vb` i `T3.vb`, określania, `Sub Main` procedurę można znaleźć w `Test2` klasy.  
  
```console
vbc t2.vb t3.vb -main:Test2  
```  
  
## <a name="see-also"></a>Zobacz także

- [Kompilator wiersza polecenia programu Visual Basic](../../../visual-basic/reference/command-line-compiler/index.md)
- [-target (Visual Basic)](../../../visual-basic/reference/command-line-compiler/target.md)
- [Przykłady kompilacji — wiersze poleceń](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)
- [Procedura główna w Visual Basic](../../../visual-basic/programming-guide/program-structure/main-procedure.md)

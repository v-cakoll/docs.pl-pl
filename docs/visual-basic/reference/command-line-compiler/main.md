---
title: -główny
ms.date: 03/13/2018
helpviewer_keywords:
- main compiler option [Visual Basic]
- /main compiler option [Visual Basic]
- -main compiler option [Visual Basic]
ms.assetid: 83fc339d-6652-415d-b205-b5133319b5b0
ms.openlocfilehash: eb9d38a7d6f74e5d8636f862c663c0ba0990baa5
ms.sourcegitcommit: c93fd5139f9efcf6db514e3474301738a6d1d649
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/27/2018
ms.locfileid: "50180235"
---
# <a name="-main"></a>-główny
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
  
 [!code-vb[VbVbalrCompiler#16](../../../visual-basic/reference/command-line-compiler/codesnippet/VisualBasic/main_1.vb)]  
  
### <a name="to-set--main-in-the-visual-studio-integrated-development-environment"></a>Aby ustawić — główny w programie Visual Studio zintegrowanego środowiska programistycznego  
  
1.  Projekt wybrany w **Eksploratora rozwiązań**. Na **projektu** menu, kliknij przycisk **właściwości**.  
  
2.  Kliknij przycisk **aplikacji** kartę.  
  
3.  Upewnij się, że **struktury aplikacji Włącz** nie zaznaczono pola wyboru.  
  
4.  Zmodyfikuj wartość w **obiekt początkowy** pole.  
  
## <a name="example"></a>Przykład  
 Poniższy kod kompiluje `T2.vb` i `T3.vb`, określania, `Sub Main` procedurę można znaleźć w `Test2` klasy.  
  
```console
vbc t2.vb t3.vb -main:Test2  
```  
  
## <a name="see-also"></a>Zobacz też  
 [Kompilator wiersza polecenia programu Visual Basic](../../../visual-basic/reference/command-line-compiler/index.md)  
 [-target (Visual Basic)](../../../visual-basic/reference/command-line-compiler/target.md)  
 [Przykłady kompilacji — wiersze poleceń](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)  
 [Procedura główna w Visual Basic](../../../visual-basic/programming-guide/program-structure/main-procedure.md)

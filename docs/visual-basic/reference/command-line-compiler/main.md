---
title: -main
ms.date: 03/13/2018
helpviewer_keywords:
- main compiler option [Visual Basic]
- /main compiler option [Visual Basic]
- -main compiler option [Visual Basic]
ms.assetid: 83fc339d-6652-415d-b205-b5133319b5b0
ms.openlocfilehash: 91f2a27ed9b6fb296dbb9e50fc488fd012311890
ms.sourcegitcommit: eff6adb61852369ab690f3f047818c90580e7eb1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/07/2019
ms.locfileid: "72005502"
---
# <a name="-main"></a>-main
Określa klasę lub moduł, który zawiera procedurę `Sub Main`.  
  
## <a name="syntax"></a>Składnia  
  
```console  
-main:location  
```  
  
## <a name="arguments"></a>Argumenty  
 `location`  
 Wymagany. Nazwa klasy lub modułu, która zawiera procedurę `Sub Main`, która ma zostać wywołana podczas uruchamiania programu. Może to być w formie **Main: module** lub **-Main: Namespace. module**.  
  
## <a name="remarks"></a>Uwagi  
 Użyj tej opcji, gdy tworzysz plik wykonywalny lub program wykonywalny systemu Windows. Jeśli opcja **-Main** zostanie pominięta, kompilator szuka prawidłowej udostępnionej `Sub Main` we wszystkich publicznych klasach i modułach.  
  
 Zapoznaj się z [główną procedurą w Visual Basic](../../../visual-basic/programming-guide/program-structure/main-procedure.md) , aby poznać różne formy procedury `Main`.  
  
 Gdy `location` jest klasą, która dziedziczy po <xref:System.Windows.Forms.Form>, kompilator udostępnia domyślną procedurę `Main`, która uruchamia aplikację, jeśli Klasa nie ma procedury `Main`. Dzięki temu można kompilować kod w wierszu polecenia, który został utworzony w środowisku programistycznym.  
  
 [!code-vb[VbVbalrCompiler#16](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrCompiler/VB/Class1.vb#16)]  
  
### <a name="to-set--main-in-the-visual-studio-integrated-development-environment"></a>Aby ustawić — Main w zintegrowanym środowisku programistycznym programu Visual Studio  
  
1. Zaznaczono projekt w **Eksplorator rozwiązań**. W menu **projekt** kliknij polecenie **Właściwości**.  
  
2. Kliknij kartę **aplikacja** .  
  
3. Upewnij się, że pole wyboru **Włącz platformę aplikacji** nie jest zaznaczone.  
  
4. Zmodyfikuj wartość w polu **obiekt startowy** .  
  
## <a name="example"></a>Przykład  
 Poniższy kod kompiluje `T2.vb` i `T3.vb`, określając, że procedura `Sub Main` zostanie znaleziona w klasie `Test2`.  
  
```console
vbc t2.vb t3.vb -main:Test2  
```  
  
## <a name="see-also"></a>Zobacz także

- [Kompilator wiersza polecenia Visual Basic](../../../visual-basic/reference/command-line-compiler/index.md)
- [-Target (Visual Basic)](../../../visual-basic/reference/command-line-compiler/target.md)
- [Przykłady kompilacji — wiersze poleceń](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)
- [Procedura Main w Visual Basic](../../../visual-basic/programming-guide/program-structure/main-procedure.md)

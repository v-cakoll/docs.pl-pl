---
title: "Porady: tworzenie właściwości (Visual Basic)"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- procedures [Visual Basic], defining
- Visual Basic code, procedures
- Visual Basic code, properties
- properties [Visual Basic]
ms.assetid: 4d229712-6be8-4c5c-bac5-06995ce9185a
caps.latest.revision: "15"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: d140e6a10061f7fabe3d12c6cce5d0c201e103d6
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-create-a-property-visual-basic"></a>Porady: tworzenie właściwości (Visual Basic)
Umieść definicji właściwości między `Property` instrukcji i `End Property` instrukcji. W ramach tej definicji zdefiniujesz `Get` procedury `Set` procedury lub oba. Wszystkie właściwości kod znajduje się w ramach tych procedur.  
  
 `Get` Procedury pobiera wartość właściwości oraz `Set` procedura przechowywana wartość. Jeśli chcesz, aby właściwość mają dostęp do odczytu/zapisu, należy zdefiniować obu tych procedur. Dla właściwości tylko do odczytu, możesz określić, tylko `Get`, dla właściwości tylko do zapisu, można określić tylko `Set`.  
  
### <a name="to-create-a-property"></a>Aby utworzyć właściwość  
  
1.  Poza właściwość lub procedura, użyj [Property — instrukcja](../../../../visual-basic/language-reference/statements/property-statement.md), a następnie `End Property` instrukcji.  
  
2.  Jeśli właściwość pobiera parametry, wykonaj `Property` — słowo kluczowe z nazwą procedury ponownie z listą parametrów w nawiasach.  
  
3.  Postępuj zgodnie z nawiasy `As` klauzuli, aby określić typ danych wartości właściwości. Należy określić typ danych, nawet w przypadku właściwości tylko do zapisu.  
  
4.  Dodaj `Get` i `Set` procedur, zależnie od potrzeb. Zobacz poniższe wskazówki.  
  
### <a name="to-create-a-get-procedure-that-retrieves-a-property-value"></a>Aby utworzyć procedura Get, który pobiera wartość właściwości  
  
1.  Między `Property` i `End Property` pisanie instrukcji [instrukcja Get](../../../../visual-basic/language-reference/statements/get-statement.md), a następnie `End Get` instrukcji. Nie trzeba definiować wszystkie parametry `Get` procedury.  
  
2.  Umieść instrukcje kodu można pobrać wartości właściwości między `Get` i `End Get` instrukcje. Ten kod może zawierać inne obliczenia i manipulacji danych oprócz generowania i zwraca wartość właściwości.  
  
3.  Użyj `Return` instrukcji, aby zwrócić wartość właściwości do wywołującego kodu.  
  
 Musisz zapisać `Get` procedury dla właściwości odczytu / zapisu, a dla właściwości tylko do odczytu. Nie można zdefiniować `Get` procedury dla właściwości tylko do zapisu.  
  
### <a name="to-create-a-set-procedure-that-writes-a-propertys-value"></a>Można utworzyć procedury zestawu, który zapisuje wartości właściwości  
  
1.  Między `Property` i `End Property` pisanie instrukcji [Instrukcja Set](../../../../visual-basic/language-reference/statements/set-statement.md), a następnie `End Set` instrukcji.  
  
2.  W `Set` instrukcji, wykonaj `Set` — słowo kluczowe z listą parametrów w nawiasach. Ta lista parametrów musi zawierać co najmniej wartość parametru wartość przekazany przez wywołującego kodu. Domyślna nazwa dla tego parametru wartość to `Value`, ale w razie potrzeby można użyć innej nazwy. Wartość parametru musi mieć taki sam typ jak samej właściwości danych.  
  
3.  Umieść instrukcje kodu do przechowywania wartości właściwości między `Set` i `End Set` instrukcje. Ten kod może zawierać inne obliczenia i manipulacji danych oprócz sprawdzania poprawności i przechowywanie wartości właściwości.  
  
4.  Aby zaakceptować wartości dostarczone przez kod wywołujący, użyj parametru wartości. Możesz zapisać tę wartość bezpośrednio w instrukcji przypisania lub używany w wyrażenie do obliczenia wartości wewnętrznego mają być przechowywane.  
  
 Musisz zapisać `Set` procedury dla właściwości odczytu / zapisu, a dla właściwości tylko do zapisu. Nie można zdefiniować `Set` procedury dla właściwości tylko do odczytu.  
  
## <a name="example"></a>Przykład  
 Poniższy przykład tworzy właściwości odczytu/zapisu, która przechowuje pełną nazwę w postaci dwóch nazw składników, imię i nazwisko. Gdy odczytuje kod wywołujący `fullName`, `Get` procedura łączy dwie nazwy składników i zwraca pełną nazwę. Gdy kod wywołujący przypisuje nową pełną nazwę, `Set` procedury próbuje podzielić dwie nazwy składowych. Jeśli nie znajdzie spację, przechowuje on wszystkie jako pierwszej nazwy.  
  
 [!code-vb[VbVbcnProcedures#8](./codesnippet/VisualBasic/how-to-create-a-property_1.vb)]  
  
 W poniższym przykładzie przedstawiono typowe wywołania procedury właściwości `fullName`. Pierwsze wywołanie ustawia wartości właściwości, a drugie wywołanie pobiera go.  
  
 [!code-vb[VbVbcnProcedures#9](./codesnippet/VisualBasic/how-to-create-a-property_2.vb)]  
  
## <a name="see-also"></a>Zobacz też  
 [Procedury](./index.md)  
 [Procedury własności](./property-procedures.md)  
 [Parametry i argumenty procedur](./procedure-parameters-and-arguments.md)  
 [Różnice pomiędzy właściwościami i zmiennymi w Visual Basic](./differences-between-properties-and-variables.md)  
 [Porady: deklarowanie właściwości z mieszanymi poziomami dostępu](./how-to-declare-a-property-with-mixed-access-levels.md)  
 [Porady: wywoływanie procedury właściwości](./how-to-call-a-property-procedure.md)  
 [Porady: deklarowanie i wywoływanie w właściwości domyślnej w Visual Basic](./how-to-declare-and-call-a-default-property.md)  
 [Porady: umieszczanie wartości we właściwości](./how-to-put-a-value-in-a-property.md)  
 [Porady: pobieranie wartości z właściwości](./how-to-get-a-value-from-a-property.md)

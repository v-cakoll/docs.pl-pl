---
title: 'Instrukcje: Tworzenie właściwości (Visual Basic)'
ms.date: 07/20/2015
helpviewer_keywords:
- procedures [Visual Basic], defining
- Visual Basic code, procedures
- Visual Basic code, properties
- properties [Visual Basic]
ms.assetid: 4d229712-6be8-4c5c-bac5-06995ce9185a
ms.openlocfilehash: 4afcd57a9133515cecc72da856f67e4e3d5ff717
ms.sourcegitcommit: 40364ded04fa6cdcb2b6beca7f68412e2e12f633
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/28/2019
ms.locfileid: "56970964"
---
# <a name="how-to-create-a-property-visual-basic"></a>Instrukcje: Tworzenie właściwości (Visual Basic)
Ujmij definicji właściwości między `Property` instrukcji i `End Property` instrukcji. W ramach tej definicji należy zdefiniować `Get` procedury `Set` procedury lub obu. Wszystkie właściwości kod znajduje się w ramach tych procedur.  
  
 `Get` Procedury pobiera wartość właściwości i `Set` procedury przechowuje wartość. Jeśli chcesz, aby właściwość mają dostęp do odczytu/zapisu, należy zdefiniować obu tych procedur. Dla właściwości tylko do odczytu, należy zdefiniować tylko `Get`, a dla właściwości tylko do zapisu, należy zdefiniować tylko `Set`.  
  
### <a name="to-create-a-property"></a>Aby utworzyć właściwość  
  
1.  Poza właściwość lub procedurę, należy użyć [Property — instrukcja](../../../../visual-basic/language-reference/statements/property-statement.md), a następnie `End Property` instrukcji.  
  
2.  Jeśli właściwość przyjmuje parametry, postępuj zgodnie z `Property` — słowo kluczowe o nazwie procedury, a następnie lista parametrów w nawiasach.  
  
3.  Postępuj zgodnie z nawiasów za pomocą `As` klauzulę, aby określić typ danych wartości właściwości. Należy określić typ danych, nawet w przypadku właściwości tylko do zapisu.  
  
4.  Dodaj `Get` i `Set` procedur, zgodnie z potrzebami. Zobacz następujące instrukcje.  
  
### <a name="to-create-a-get-procedure-that-retrieves-a-property-value"></a>Aby utworzyć procedurę Get, który pobiera wartość właściwości  
  
1.  Między `Property` i `End Property` pisanie instrukcji [instrukcja Get](../../../../visual-basic/language-reference/statements/get-statement.md), a następnie `End Get` instrukcji. Nie musisz zdefiniować inne parametry `Get` procedury.  
  
2.  Umieść instrukcje kodu, który można pobrać wartości właściwości między `Get` i `End Get` instrukcji. Ten kod może zawierać innych obliczeń i manipulacji danych oprócz generowania i zwracanie wartości właściwości.  
  
3.  Użyj `Return` instrukcji, aby zwrócić wartości właściwości do wywołującego kodu.  
  
 Należy napisać `Get` procedury dla właściwości odczytu / zapisu, a dla właściwości tylko do odczytu. Nie można zdefiniować `Get` procedury dla właściwości tylko do zapisu.  
  
### <a name="to-create-a-set-procedure-that-writes-a-propertys-value"></a>Aby utworzyć procedurę zestaw, który zapisuje wartości właściwości  
  
1.  Między `Property` i `End Property` pisanie instrukcji [instrukcji Set](../../../../visual-basic/language-reference/statements/set-statement.md), a następnie `End Set` instrukcji.  
  
2.  W `Set` instrukcji, postępuj zgodnie z `Set` — słowo kluczowe z listą parametrów w nawiasach. Ta lista parametrów musi zawierać co najmniej jeden parametr wartości dla wartości przekazywane przez kod wywołujący. Domyślną nazwą tego wartość parametru jest `Value`, ale można użyć innej nazwy, jeśli to stosowne. Parametr wartość musi mieć taki sam typ jako samej właściwości danych.  
  
3.  Umieść instrukcje kodu, do przechowywania wartości właściwości między `Set` i `End Set` instrukcji. Ten kod może zawierać innych obliczeń i manipulacji danych oprócz sprawdzania poprawności i przechowywania wartości właściwości.  
  
4.  Aby zaakceptować wartość dostarczona przez kod wywołujący, należy użyć parametru wartości. Możesz zapisać tę wartość bezpośrednio w instrukcji przypisania lub używany w atakach wyrażenie do obliczenia wartości wewnętrznej, które mają być przechowywane.  
  
 Należy napisać `Set` procedury dla właściwości odczytu / zapisu, a dla właściwości tylko do zapisu. Nie można zdefiniować `Set` procedury dla właściwości tylko do odczytu.  
  
## <a name="example"></a>Przykład  
 Poniższy przykład tworzy właściwości odczytu/zapisu, która przechowuje pełną nazwę w postaci dwóch nazw składowych, imię i nazwisko. Podczas wywoływania kodu odczytuje `fullName`, `Get` procedury łączy dwie nazwy składowych i zwraca pełną nazwę. Gdy kod wywołujący przypisuje nową pełną nazwę, `Set` procedury próbuje podzielenie go na dwie nazwy składowych. Jeśli nie znajdzie spację, przechowuje on wszystkie jako imię.  
  
 [!code-vb[VbVbcnProcedures#8](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#8)]  
  
 W poniższym przykładzie przedstawiono typowe wywołania procedur właściwość `fullName`. Pierwsze wywołanie ustawia wartości właściwości, a drugie wywołanie pobiera je.  
  
 [!code-vb[VbVbcnProcedures#9](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#9)]  
  
## <a name="see-also"></a>Zobacz także
- [Procedury](./index.md)
- [Procedury właściwości](./property-procedures.md)
- [Parametry i argumenty procedur](./procedure-parameters-and-arguments.md)
- [Różnice między właściwościami i zmiennymi w Visual Basic](./differences-between-properties-and-variables.md)
- [Instrukcje: Deklarowanie właściwości z mieszanymi poziomami dostępu](./how-to-declare-a-property-with-mixed-access-levels.md)
- [Instrukcje: Wywoływanie procedury właściwości](./how-to-call-a-property-procedure.md)
- [Instrukcje: Deklarowanie i wywoływanie w właściwości domyślnej w języku Visual Basic](./how-to-declare-and-call-a-default-property.md)
- [Instrukcje: Umieszczanie wartości we właściwości](./how-to-put-a-value-in-a-property.md)
- [Instrukcje: Pobieranie wartości z właściwości](./how-to-get-a-value-from-a-property.md)

---
title: 'Porady: tworzenie właściwości'
ms.date: 07/20/2015
helpviewer_keywords:
- procedures [Visual Basic], defining
- Visual Basic code, procedures
- Visual Basic code, properties
- properties [Visual Basic]
ms.assetid: 4d229712-6be8-4c5c-bac5-06995ce9185a
ms.openlocfilehash: ee5a9f687765ce064eb3c3f84218ed36eb916d9d
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/22/2019
ms.locfileid: "74349700"
---
# <a name="how-to-create-a-property-visual-basic"></a>Porady: tworzenie właściwości (Visual Basic)
Należy ująć definicję właściwości między instrukcją `Property` a instrukcją `End Property`. W ramach tej definicji zdefiniujesz procedurę `Get`, procedurę `Set` lub obie. Wszystkie kody właściwości są w tych procedurach.  
  
 Procedura `Get` Pobiera wartość właściwości, a procedura `Set` przechowuje wartość. Jeśli chcesz, aby Właściwość miała dostęp do odczytu/zapisu, musisz zdefiniować obie procedury. Dla właściwości tylko do odczytu definiuje się tylko `Get`i dla właściwości tylko do zapisu, definiuje się tylko `Set`.  
  
### <a name="to-create-a-property"></a>Aby utworzyć właściwość  
  
1. Poza dowolnymi właściwościami lub procedurami Użyj [instrukcji właściwości](../../../../visual-basic/language-reference/statements/property-statement.md), a po niej instrukcji `End Property`.  
  
2. Jeśli właściwość przyjmuje parametry, należy postępować według słowa kluczowego `Property` z nazwą procedury, a następnie na liście parametrów w nawiasach.  
  
3. Użyj nawiasów z klauzulą `As`, aby określić typ danych wartości właściwości. Należy określić typ danych nawet dla właściwości tylko do zapisu.  
  
4. W razie potrzeby Dodaj procedury `Get` i `Set`. Zapoznaj się z następującymi wskazówkami.  
  
### <a name="to-create-a-get-procedure-that-retrieves-a-property-value"></a>Aby utworzyć procedurę Get, która pobiera wartość właściwości  
  
1. Między instrukcjami `Property` i `End Property` Napisz [instrukcję Get](../../../../visual-basic/language-reference/statements/get-statement.md), a następnie instrukcję `End Get`. Nie trzeba definiować żadnych parametrów dla procedury `Get`.  
  
2. Umieść instrukcje Code, aby pobrać wartość właściwości między instrukcjami `Get` i `End Get`. Ten kod może obejmować inne obliczenia i manipulowanie danymi, a także generowanie i zwracanie wartości właściwości.  
  
3. Użyj instrukcji `Return`, aby zwrócić wartość właściwości do kodu wywołującego.  
  
 Należy napisać `Get` procedury dla właściwości Read-Write i dla właściwości tylko do odczytu. Nie należy definiować `Get` procedury dla właściwości tylko do zapisu.  
  
### <a name="to-create-a-set-procedure-that-writes-a-propertys-value"></a>Aby utworzyć procedurę zestawu, która zapisuje wartość właściwości  
  
1. Między instrukcjami `Property` i `End Property` Napisz [instrukcję SET](../../../../visual-basic/language-reference/statements/set-statement.md), po której następuje instrukcja `End Set`.  
  
2. W instrukcji `Set` postępuj według słowa kluczowego `Set` z listą parametrów w nawiasach. Ta lista parametrów musi zawierać co najmniej parametr wartości dla wartości przesłanej przez wywoływany kod. Domyślna nazwa dla tego parametru wartości to `Value`, ale w razie potrzeby można użyć innej nazwy. Parametr value musi mieć ten sam typ danych co sama właściwość.  
  
3. Umieść instrukcje Code w celu zapisania wartości we właściwości między instrukcjami `Set` i `End Set`. Ten kod może obejmować inne obliczenia i manipulowanie danymi, a także sprawdzanie poprawności i przechowywanie wartości właściwości.  
  
4. Użyj parametru value, aby zaakceptować wartość podaną przez wywołujący kod. Tę wartość można przechowywać bezpośrednio w instrukcji przypisania lub użyć jej w wyrażeniu w celu obliczenia wartości wewnętrznej do zapisania.  
  
 Należy napisać `Set` procedury dla właściwości Read-Write i dla właściwości tylko do zapisu. Nie należy definiować `Set` procedury dla właściwości tylko do odczytu.  
  
## <a name="example"></a>Przykład  
 Poniższy przykład tworzy właściwość odczytu/zapisu, która przechowuje pełną nazwę jako dwie nazwy składników, imię i nazwisko. Gdy wywołujący kod odczytuje `fullName`, procedura `Get` łączy dwa nazwy składników i zwraca pełną nazwę. Gdy wywołujący kod przypisze nową pełną nazwę, procedura `Set` próbuje podzielić ją na dwie nazwy składników. Jeśli nie znajdzie miejsca, będzie ono przechowywane jako imię i nazwisko.  
  
 [!code-vb[VbVbcnProcedures#8](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#8)]  
  
 W poniższym przykładzie przedstawiono typowe wywołania procedur właściwości `fullName`. Pierwsze wywołanie ustawia wartość właściwości i drugie wywołanie pobiera je.  
  
 [!code-vb[VbVbcnProcedures#9](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#9)]  
  
## <a name="see-also"></a>Zobacz także

- [Procedury](./index.md)
- [Procedury właściwości](./property-procedures.md)
- [Parametry i argumenty procedur](./procedure-parameters-and-arguments.md)
- [Różnice między właściwościami i zmiennymi w Visual Basic](./differences-between-properties-and-variables.md)
- [Instrukcje: deklarowanie właściwości z mieszanymi poziomami dostępu](./how-to-declare-a-property-with-mixed-access-levels.md)
- [Instrukcje: wywoływanie procedury właściwości](./how-to-call-a-property-procedure.md)
- [Instrukcje: deklarowanie i wywoływanie właściwości domyślnej w Visual Basic](./how-to-declare-and-call-a-default-property.md)
- [Instrukcje: umieszczanie wartości we właściwości](./how-to-put-a-value-in-a-property.md)
- [Instrukcje: pobieranie wartości z właściwości](./how-to-get-a-value-from-a-property.md)

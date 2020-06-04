---
title: 'Porady: tworzenie właściwości'
ms.date: 07/20/2015
helpviewer_keywords:
- procedures [Visual Basic], defining
- Visual Basic code, procedures
- Visual Basic code, properties
- properties [Visual Basic]
ms.assetid: 4d229712-6be8-4c5c-bac5-06995ce9185a
ms.openlocfilehash: fa220998d12206e620c242b9b39df3dc1b639d29
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/04/2020
ms.locfileid: "84388261"
---
# <a name="how-to-create-a-property-visual-basic"></a>Porady: tworzenie właściwości (Visual Basic)
Należy ująć definicję właściwości między `Property` instrukcją a `End Property` instrukcją. W ramach tej definicji należy zdefiniować `Get` procedurę, `Set` procedurę lub oba te elementy. Wszystkie kody właściwości są w tych procedurach.  
  
 `Get`Procedura Pobiera wartość właściwości, a `Set` procedura przechowuje wartość. Jeśli chcesz, aby Właściwość miała dostęp do odczytu/zapisu, musisz zdefiniować obie procedury. Dla właściwości tylko do odczytu należy zdefiniować tylko `Get` i dla właściwości tylko do zapisu `Set` .  
  
### <a name="to-create-a-property"></a>Aby utworzyć właściwość  
  
1. Poza dowolnymi właściwościami lub procedurami Użyj [instrukcji właściwości](../../../language-reference/statements/property-statement.md), a po niej `End Property` instrukcji.  
  
2. Jeśli właściwość przyjmuje parametry, należy użyć `Property` słowa kluczowego z nazwą procedury, a następnie na liście parametrów w nawiasach.  
  
3. Postępuj zgodnie z nawiasami z `As` klauzulą, aby określić typ danych wartości właściwości. Należy określić typ danych nawet dla właściwości tylko do zapisu.  
  
4. Dodaj `Get` `Set` procedury i w razie potrzeby. Zapoznaj się z następującymi wskazówkami.  
  
### <a name="to-create-a-get-procedure-that-retrieves-a-property-value"></a>Aby utworzyć procedurę Get, która pobiera wartość właściwości  
  
1. Między `Property` instrukcjami i `End Property` Napisz [instrukcję Get](../../../language-reference/statements/get-statement.md), a po niej `End Get` instrukcję. Nie trzeba definiować żadnych parametrów dla `Get` procedury.  
  
2. Umieść instrukcje Code, aby pobrać wartość właściwości między `Get` `End Get` instrukcjami i. Ten kod może obejmować inne obliczenia i manipulowanie danymi, a także generowanie i zwracanie wartości właściwości.  
  
3. Użyj `Return` instrukcji, aby zwrócić wartość właściwości do kodu wywołującego.  
  
 Należy napisać `Get` procedurę dla właściwości Read-Write i dla właściwości tylko do odczytu. Nie należy definiować `Get` procedury dla właściwości tylko do zapisu.  
  
### <a name="to-create-a-set-procedure-that-writes-a-propertys-value"></a>Aby utworzyć procedurę zestawu, która zapisuje wartość właściwości  
  
1. Między `Property` instrukcjami i `End Property` Napisz [instrukcję SET](../../../language-reference/statements/set-statement.md), a po niej `End Set` instrukcję.  
  
2. W `Set` instrukcji postępuj według `Set` słowa kluczowego z listą parametrów w nawiasach. Ta lista parametrów musi zawierać co najmniej parametr wartości dla wartości przesłanej przez wywoływany kod. Domyślną nazwą dla tego parametru wartości jest `Value` , ale w razie potrzeby można użyć innej nazwy. Parametr value musi mieć ten sam typ danych co sama właściwość.  
  
3. Umieść instrukcje Code w celu zapisania wartości we właściwości między `Set` `End Set` instrukcjami i. Ten kod może obejmować inne obliczenia i manipulowanie danymi, a także sprawdzanie poprawności i przechowywanie wartości właściwości.  
  
4. Użyj parametru value, aby zaakceptować wartość podaną przez wywołujący kod. Tę wartość można przechowywać bezpośrednio w instrukcji przypisania lub użyć jej w wyrażeniu w celu obliczenia wartości wewnętrznej do zapisania.  
  
 Należy napisać `Set` procedurę dla właściwości Read-Write i dla właściwości tylko do zapisu. Nie należy definiować `Set` procedury dla właściwości tylko do odczytu.  
  
## <a name="example"></a>Przykład  
 Poniższy przykład tworzy właściwość odczytu/zapisu, która przechowuje pełną nazwę jako dwie nazwy składników, imię i nazwisko. Podczas odczytywania kodu wywołującego `fullName` `Get` procedura łączy dwie nazwy składników i zwraca pełną nazwę. Gdy wywołujący kod przypisze nową pełną nazwę, `Set` procedura próbuje ją podzielić na dwie nazwy składników. Jeśli nie znajdzie miejsca, będzie ono przechowywane jako imię i nazwisko.  
  
 [!code-vb[VbVbcnProcedures#8](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#8)]  
  
 W poniższym przykładzie przedstawiono typowe wywołania procedur właściwości `fullName` . Pierwsze wywołanie ustawia wartość właściwości i drugie wywołanie pobiera je.  
  
 [!code-vb[VbVbcnProcedures#9](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#9)]  
  
## <a name="see-also"></a>Zobacz też

- [Procedury](./index.md)
- [Procedury własności](./property-procedures.md)
- [Parametry i argumenty procedur](./procedure-parameters-and-arguments.md)
- [Różnice pomiędzy właściwościami i zmiennymi w Visual Basic](./differences-between-properties-and-variables.md)
- [Porady: deklarowanie właściwości z mieszanymi poziomami dostępu](./how-to-declare-a-property-with-mixed-access-levels.md)
- [Porady: wywoływanie procedury właściwości](./how-to-call-a-property-procedure.md)
- [Porady: deklarowanie i wywoływanie w właściwości domyślnej w Visual Basic](./how-to-declare-and-call-a-default-property.md)
- [Instrukcje: umieszczanie wartości we właściwości](./how-to-put-a-value-in-a-property.md)
- [Instrukcje: pobieranie wartości z właściwości](./how-to-get-a-value-from-a-property.md)

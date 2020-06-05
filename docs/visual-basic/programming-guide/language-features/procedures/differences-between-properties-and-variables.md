---
title: Różnice między właściwościami i zmiennymi
ms.date: 07/20/2015
helpviewer_keywords:
- property values [Visual Basic]
- variables [Visual Basic]
- Visual Basic code, procedures
- values [Visual Basic], properties
- variables [Visual Basic], definition
- Visual Basic code, variables
- Visual Basic code, properties
- properties [Visual Basic], values
- properties [Visual Basic], defined
- variables [Visual Basic], and properties
- properties [Visual Basic], and variables
ms.assetid: 7a03a8be-5381-431f-bd7c-16e887e4e07b
ms.openlocfilehash: 162bd71eaebdf55f6be89e0c5dce7acc1b975d79
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/04/2020
ms.locfileid: "84403307"
---
# <a name="differences-between-properties-and-variables-in-visual-basic"></a>Różnice pomiędzy właściwościami i zmiennymi w Visual Basic
Zmienne i właściwości reprezentują wartości, do których można uzyskać dostęp. Istnieją jednak różnice dotyczące magazynu i implementacji.  
  
## <a name="variables"></a>Zmienne  
 *Zmienna* odnosi się bezpośrednio do lokalizacji w pamięci. Należy zdefiniować zmienną z pojedynczą instrukcją deklaracji. Zmienna może być *zmienną lokalną*, zdefiniowaną wewnątrz procedury i dostępną tylko w ramach tej procedury lub może być *zmienną członkowską*, zdefiniowaną w module, klasie lub strukturze, ale nie wewnątrz żadnej procedury. Zmienna członkowska jest również wywoływana jako *pole*.  
  
## <a name="properties"></a>Właściwości  
 *Właściwość* jest elementem danych zdefiniowanym dla modułu, klasy lub struktury. Należy zdefiniować właściwość z blokiem kodu między `Property` `End Property` instrukcjami i. Blok kodu zawiera `Get` procedurę, `Set` procedurę lub obie te metody. Te procedury są nazywane *procedurami właściwości* lub metodami *dostępu do właściwości*. Oprócz pobierania lub przechowywania wartości właściwości, mogą również wykonywać akcje niestandardowe, takie jak aktualizowanie licznika dostępu.  
  
## <a name="differences"></a>Różnice  
 W poniższej tabeli przedstawiono kilka ważnych różnic między zmiennymi i właściwościami.  
  
|Punkt różnicy|Zmienna|Właściwość|  
|-------------------------|--------------|--------------|  
|Oświadczeń|Single deklaracji — instrukcja|Seria instrukcji w bloku kodu|  
|Implementacja|Lokalizacja jednego magazynu|Kod wykonywalny (procedury właściwości)|  
|Magazyn|Bezpośrednio skojarzone z wartością zmiennej|Zwykle magazyn wewnętrzny nie jest dostępny poza klasą lub modułem zawierającym Właściwość<br /><br /> Wartość właściwości może być lub nie istnieć jako składowa elementu <sup>1</sup>|  
|Kod wykonywalny|Brak|Musi zawierać co najmniej jedną procedurę|  
|Dostęp do odczytu i zapisu|Odczyt/zapis lub tylko do odczytu|Odczyt/zapis, tylko do odczytu lub tylko do zapisu|  
|Akcje niestandardowe (oprócz akceptowania lub zwracania wartości)|Niemożliwe|Można wykonać jako część ustawienia lub pobrać wartość właściwości|  
  
 <sup>1</sup> w przeciwieństwie do zmiennej, wartość właściwości może nie odpowiadać bezpośrednio na pojedynczy element magazynu. Magazyn może być podzielony na fragmenty dla wygody lub bezpieczeństwa lub wartość może być przechowywana w postaci zaszyfrowanej. W takich przypadkach `Get` procedura może złożyć fragmenty lub odszyfrować przechowywaną wartość, a `Set` procedura będzie szyfrować nową wartość lub podzielić ją na magazyn elementów składowych. Wartość właściwości może być wyliczeniem nieulotnym, takim jak godzina dnia, w którym to przypadku `Get` procedura będzie obliczać ją na bieżąco za każdym razem, gdy uzyskujesz dostęp do właściwości.  
  
## <a name="see-also"></a>Zobacz też

- [Procedury własności](./property-procedures.md)
- [Parametry i argumenty procedur](./procedure-parameters-and-arguments.md)
- [Property — Instrukcja](../../../language-reference/statements/property-statement.md)
- [Dim, instrukcja](../../../language-reference/statements/dim-statement.md)
- [Instrukcje: tworzenie właściwości](./how-to-create-a-property.md)
- [Porady: deklarowanie właściwości z mieszanymi poziomami dostępu](./how-to-declare-a-property-with-mixed-access-levels.md)
- [Porady: wywoływanie procedury właściwości](./how-to-call-a-property-procedure.md)
- [Porady: deklarowanie i wywoływanie w właściwości domyślnej w Visual Basic](./how-to-declare-and-call-a-default-property.md)
- [Instrukcje: umieszczanie wartości we właściwości](./how-to-put-a-value-in-a-property.md)
- [Instrukcje: pobieranie wartości z właściwości](./how-to-get-a-value-from-a-property.md)

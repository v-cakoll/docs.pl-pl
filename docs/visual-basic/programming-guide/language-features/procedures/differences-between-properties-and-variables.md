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
ms.openlocfilehash: bbed3248840803d36607a67c8373fed15c07445f
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/22/2019
ms.locfileid: "74341221"
---
# <a name="differences-between-properties-and-variables-in-visual-basic"></a>Różnice pomiędzy właściwościami i zmiennymi w Visual Basic
Zmienne i właściwości reprezentują wartości, do których można uzyskać dostęp. Istnieją jednak różnice dotyczące magazynu i implementacji.  
  
## <a name="variables"></a>Zmienne  
 *Zmienna* odnosi się bezpośrednio do lokalizacji w pamięci. Należy zdefiniować zmienną z pojedynczą instrukcją deklaracji. Zmienna może być *zmienną lokalną*, zdefiniowaną wewnątrz procedury i dostępną tylko w ramach tej procedury lub może być *zmienną członkowską*, zdefiniowaną w module, klasie lub strukturze, ale nie wewnątrz żadnej procedury. Zmienna członkowska jest również wywoływana jako *pole*.  
  
## <a name="properties"></a>Właściwości  
 *Właściwość* jest elementem danych zdefiniowanym dla modułu, klasy lub struktury. Należy zdefiniować właściwość z blokiem kodu między instrukcjami `Property` i `End Property`. Blok kodu zawiera procedurę `Get`, procedurę `Set` lub obie te metody. Te procedury są nazywane *procedurami właściwości* lub metodami *dostępu do właściwości*. Oprócz pobierania lub przechowywania wartości właściwości, mogą również wykonywać akcje niestandardowe, takie jak aktualizowanie licznika dostępu.  
  
## <a name="differences"></a>Wynikających  
 W poniższej tabeli przedstawiono kilka ważnych różnic między zmiennymi i właściwościami.  
  
|Punkt różnicy|Zmienna|Właściwość|  
|-------------------------|--------------|--------------|  
|Oświadczeń|Single deklaracji — instrukcja|Seria instrukcji w bloku kodu|  
|Implementacja|Lokalizacja jednego magazynu|Kod wykonywalny (procedury właściwości)|  
|Magazyn|Bezpośrednio skojarzone z wartością zmiennej|Zwykle magazyn wewnętrzny nie jest dostępny poza klasą lub modułem zawierającym Właściwość<br /><br /> Wartość właściwości może być lub nie istnieć jako składowa elementu <sup>1</sup>|  
|Kod wykonywalny|Brak|Musi zawierać co najmniej jedną procedurę|  
|Dostęp do odczytu i zapisu|Odczyt/zapis lub tylko do odczytu|Odczyt/zapis, tylko do odczytu lub tylko do zapisu|  
|Akcje niestandardowe (oprócz akceptowania lub zwracania wartości)|Niemożliwa|Można wykonać jako część ustawienia lub pobrać wartość właściwości|  
  
 <sup>1</sup> w przeciwieństwie do zmiennej, wartość właściwości może nie odpowiadać bezpośrednio na pojedynczy element magazynu. Magazyn może być podzielony na fragmenty dla wygody lub bezpieczeństwa lub wartość może być przechowywana w postaci zaszyfrowanej. W takich przypadkach procedura `Get` może złożyć fragmenty lub odszyfrować przechowywaną wartość, a procedura `Set` zaszyfruje nową wartość lub wyodrębni ją do magazynu elementów. Wartość właściwości może być wyliczeniem nieulotnym, takim jak czas dnia, a w takim przypadku procedura `Get` będzie obliczać ją na bieżąco przy każdej próbie uzyskania dostępu do właściwości.  
  
## <a name="see-also"></a>Zobacz także

- [Procedury właściwości](./property-procedures.md)
- [Parametry i argumenty procedur](./procedure-parameters-and-arguments.md)
- [Property, instrukcja](../../../../visual-basic/language-reference/statements/property-statement.md)
- [Dim, instrukcja](../../../../visual-basic/language-reference/statements/dim-statement.md)
- [Instrukcje: tworzenie właściwości](./how-to-create-a-property.md)
- [Instrukcje: deklarowanie właściwości z mieszanymi poziomami dostępu](./how-to-declare-a-property-with-mixed-access-levels.md)
- [Instrukcje: wywoływanie procedury właściwości](./how-to-call-a-property-procedure.md)
- [Instrukcje: deklarowanie i wywoływanie właściwości domyślnej w Visual Basic](./how-to-declare-and-call-a-default-property.md)
- [Instrukcje: umieszczanie wartości we właściwości](./how-to-put-a-value-in-a-property.md)
- [Instrukcje: pobieranie wartości z właściwości](./how-to-get-a-value-from-a-property.md)

---
title: Różnice pomiędzy właściwościami i zmiennymi w Visual Basic
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
ms.openlocfilehash: de4800e23519c2cc1c8b2b219287b9fa018b9bbf
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/18/2019
ms.locfileid: "58842905"
---
# <a name="differences-between-properties-and-variables-in-visual-basic"></a>Różnice pomiędzy właściwościami i zmiennymi w Visual Basic
Zmienne i właściwości reprezentują wartości, do których masz dostęp. Jednak istnieją różnice w pamięci masowej i implementacji.  
  
## <a name="variables"></a>Zmienne  
 A *zmiennej* odnosi się bezpośrednio do lokalizacji w pamięci. Należy zdefiniować zmienną z instrukcją jednej deklaracji. Zmienna może być *zmienna lokalna*, zdefiniowane wewnątrz procedury i jest dostępna tylko w ramach tej procedury, lub może być *zmiennej składowej*, zdefiniowane w module, klasy lub struktury, ale nie wewnątrz każdego procedura. Zmienna członka jest również nazywany *pola*.  
  
## <a name="properties"></a>Właściwości  
 A *właściwość* jest elementem danych zdefiniowanych dla modułu, klasy lub struktury. Zdefiniuj właściwość z blokiem kodu między `Property` i `End Property` instrukcji. Blok kodu zawiera `Get` procedury `Set` procedury lub obu. Te procedury są nazywane *procedury właściwości* lub *Akcesory właściwości*. Oprócz pobierania lub zapisywania wartości właściwości, mogą również wykonać akcje niestandardowe, takie jak aktualizowanie licznika dostępu.  
  
## <a name="differences"></a>Różnice  
 Poniższej tabeli przedstawiono kilka istotnych różnic między zmienne i właściwości.  
  
|Punkcie różnicę|Zmienna|Właściwość|  
|-------------------------|--------------|--------------|  
|Deklaracja|Instrukcja jednej deklaracji|Serię instrukcji w bloku kodu|  
|Implementacja|Pojedynczy magazyn lokalizacji|Kod wykonywalny (procedury właściwości)|  
|Magazyn|Bezpośrednio kojarzone z wartość zmiennej|Zwykle ma wewnętrzny magazyn nie jest dostępna spoza klasę lub moduł zawierający właściwości<br /><br /> Wartość właściwości może lub nie istnieje jako element przechowywanych <sup>1</sup>|  
|Kod wykonywalny|Brak|Musi mieć co najmniej jednej procedury|  
|Odczyt i zapis|Odczyt/zapis lub tylko do odczytu|Odczytu/zapisu, tylko do odczytu lub tylko do zapisu|  
|Akcje niestandardowe (oprócz akceptować lub zwracania wartości)|Nie jest możliwe|Mogą być wykonywane w ramach ustawiania i pobierania wartości właściwości|  
  
 <sup>1</sup> w przeciwieństwie do zmiennej, wartość właściwości nie może odpowiadać bezpośrednio do jednego elementu magazynu. Magazyn może zostać podzielony na fragmenty dla wygody lub zabezpieczeń, lub wartość mogą być przechowywane w postaci zaszyfrowanej. W takich przypadkach `Get` procedury może tworzyć elementy lub odszyfrować przechowywaną wartość i `Set` procedury czy szyfrowanie nową wartość lub podzielić składników magazynu. Wartości właściwości mogą być efemeryczne, takich jak porę dnia, w którym to przypadku `Get` procedury może obliczyć go na bieżąco zawsze dostęp do właściwości.  
  
## <a name="see-also"></a>Zobacz także

- [Procedury właściwości](./property-procedures.md)
- [Parametry i argumenty procedur](./procedure-parameters-and-arguments.md)
- [Instrukcja Property](../../../../visual-basic/language-reference/statements/property-statement.md)
- [Dim, instrukcja](../../../../visual-basic/language-reference/statements/dim-statement.md)
- [Instrukcje: Tworzenie właściwości](./how-to-create-a-property.md)
- [Instrukcje: Deklarowanie właściwości z mieszanymi poziomami dostępu](./how-to-declare-a-property-with-mixed-access-levels.md)
- [Instrukcje: Wywoływanie procedury właściwości](./how-to-call-a-property-procedure.md)
- [Instrukcje: Deklarowanie i wywoływanie w właściwości domyślnej w języku Visual Basic](./how-to-declare-and-call-a-default-property.md)
- [Instrukcje: Umieszczanie wartości we właściwości](./how-to-put-a-value-in-a-property.md)
- [Instrukcje: Pobieranie wartości z właściwości](./how-to-get-a-value-from-a-property.md)

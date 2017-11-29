---
title: "Różnice pomiędzy właściwościami i zmiennymi w Visual Basic"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
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
caps.latest.revision: "14"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: cb30972e2b49a7005749f57c0223b9fa493cde52
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="differences-between-properties-and-variables-in-visual-basic"></a>Różnice pomiędzy właściwościami i zmiennymi w Visual Basic
Zmienne i właściwości reprezentują wartości, które są dostępne. Istnieją różnice w pamięci masowej i implementacji.  
  
## <a name="variables"></a>Zmienne  
 A *zmiennej* odpowiada bezpośrednio do lokalizacji w pamięci. Należy zdefiniować zmienną z instrukcją jednej deklaracji. Może być zmienną *zmiennej lokalnej*, zdefiniowane wewnątrz procedury i jest dostępny tylko w ramach tej procedury, lub można ją *zmiennej członkowskiej*, zdefiniowane w module, klasy lub struktury, ale nie znajduje się w dowolnej procedury. Zmiennej członkowskiej jest również nazywany *pola*.  
  
## <a name="properties"></a>Właściwości  
 A *właściwości* jest elementem dane zdefiniowane dla modułu, klasy lub struktury. Definiuje właściwości z bloku kodu między `Property` i `End Property` instrukcje. Blok kodu zawiera `Get` procedury `Set` procedury lub oba. Te procedury są nazywane *procedury właściwości* lub *metod dostępu do właściwości*. Oprócz pobierania lub przechowywania wartość właściwości, one również wykonywać akcje niestandardowe, takie jak aktualizowanie licznika dostępu.  
  
## <a name="differences"></a>Różnice  
 W poniższej tabeli przedstawiono kilka istotnych różnic między zmiennych i właściwości.  
  
|Punktu różnicy|Zmienna|Właściwość|  
|-------------------------|--------------|--------------|  
|Deklaracja|Pojedyncza deklaracja — instrukcja|Seria instrukcje w bloku kodu|  
|Implementacja|Pojedyncze magazynu|Kod wykonywalny (procedury właściwości)|  
|Magazyn|Bezpośrednio związane z wartość zmiennej|Zwykle ma pamięci wewnętrznej nie jest dostępny poza klasę lub moduł zawierający właściwości<br /><br /> Wartość właściwości może lub nie istnieje jako element przechowywanych <sup>1</sup>|  
|Kod wykonywalny|Brak|Musi mieć co najmniej jednej procedury|  
|Odczyt i zapis|Odczyt i zapis czy tylko do odczytu|Odczyt/zapis, tylko do odczytu lub w trybie tylko do zapisu|  
|Akcje niestandardowe (oprócz akceptowanie lub zwracania wartości)|Nie jest możliwe|Można wykonać w ramach ustawiania i pobierania wartości właściwości|  
  
 <sup>1</sup> w przeciwieństwie do zmiennej, wartość właściwości nie może odpowiadać bezpośrednio do pojedynczego elementu magazynu. Magazyn może zostać podzielony na fragmenty dla wygody lub zabezpieczeń, lub wartość mogą być przechowywane w postaci zaszyfrowanej. W takich przypadkach `Get` procedury czy złożyć części lub odszyfrować przechowywana wartość i `Set` procedury czy szyfrowania nowej wartości lub podziel go na składników magazynu. Wartości właściwości mogą być efemeryczne, takich jak porę dnia, w którym to przypadku `Get` procedury będzie obliczać go na bieżąco zawsze dostęp do właściwości.  
  
## <a name="see-also"></a>Zobacz też  
 [Procedury własności](./property-procedures.md)  
 [Parametry i argumenty procedur](./procedure-parameters-and-arguments.md)  
 [Property — instrukcja](../../../../visual-basic/language-reference/statements/property-statement.md)  
 [Dim — instrukcja](../../../../visual-basic/language-reference/statements/dim-statement.md)  
 [Porady: Tworzenie właściwości](./how-to-create-a-property.md)  
 [Porady: deklarowanie właściwości z mieszanymi poziomami dostępu](./how-to-declare-a-property-with-mixed-access-levels.md)  
 [Porady: wywoływanie procedury właściwości](./how-to-call-a-property-procedure.md)  
 [Porady: deklarowanie i wywoływanie w właściwości domyślnej w Visual Basic](./how-to-declare-and-call-a-default-property.md)  
 [Porady: umieszczanie wartości we właściwości](./how-to-put-a-value-in-a-property.md)  
 [Porady: pobieranie wartości z właściwości](./how-to-get-a-value-from-a-property.md)

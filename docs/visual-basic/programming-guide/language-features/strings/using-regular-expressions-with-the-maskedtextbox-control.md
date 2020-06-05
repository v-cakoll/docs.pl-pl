---
title: Używanie wyrażeń regularnych z kontrolką MaskedTextBox
ms.date: 07/20/2015
helpviewer_keywords:
- strings [Visual Basic], regular expressions
- strings [Visual Basic], masked edit
ms.assetid: 2a048fb0-7053-487d-b2c5-ffa5e22ed6f9
ms.openlocfilehash: efda70be0ccdbc1f4b59d548e50f743f6c493b19
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/04/2020
ms.locfileid: "84363719"
---
# <a name="using-regular-expressions-with-the-maskedtextbox-control-in-visual-basic"></a>Używanie wyrażeń regularnych z formantem MaskedTextBox w Visual Basic
W tym przykładzie pokazano, jak konwertować proste wyrażenia regularne do pracy z <xref:System.Windows.Forms.MaskedTextBox> kontrolką.  
  
## <a name="description-of-the-masking-language"></a>Opis języka maskowania  
 Standardowy <xref:System.Windows.Forms.MaskedTextBox> Język maskujący jest oparty na tym, kto jest używany przez `Masked Edit` formant w Visual Basic 6,0 i powinien być zaznajomiony z użytkownikami migrowania z tej platformy.  
  
 <xref:System.Windows.Forms.MaskedTextBox.Mask%2A>Właściwość <xref:System.Windows.Forms.MaskedTextBox> kontrolki określa, która Maska wprowadzania ma być używana. Maska musi być ciągiem składającym się z co najmniej jednego elementu maskowania z poniższej tabeli.  
  
|Maskowanie elementu|Opis|Element wyrażenia regularnego|  
|---------------------|-----------------|--------------------------------|  
|0|Dowolna pojedyncza cyfra z przedziału od 0 do 9. Wpis jest wymagany.|\d|  
|9|Cyfra lub spacja. Wpis opcjonalny.|[\d]?|  
|#|Cyfra lub spacja. Wpis opcjonalny. W przypadku pozostawienia pustej pozycji w masce zostanie ona renderowana jako spacja. Znaki plus (+) i minus (-) są dozwolone.|[\d +-]?|  
|L|Litera ASCII. Wpis jest wymagany.|[a-za-Z]|  
|?|Litera ASCII. Wpis opcjonalny.|[a-za-Z]?|  
|&|Opis. Wpis jest wymagany.|[\p{Ll}\p{Lu}\p{Lt}\p{Lm}\p{Lo}]|  
|C|Opis. Wpis opcjonalny.|[\p{Ll}\p{Lu}\p{Lt}\p{Lm}\p{Lo}]?|  
|A|Pełnej. Wpis opcjonalny.|\W|  
|.|Odpowiedni symbol zastępczy dziesiętnej kultury.|Niedostępne.|  
|,|Symbol zastępczy tysięcy odpowiednich kultur.|Niedostępne.|  
|:|Separator czasu odpowiedni dla kultury.|Niedostępne.|  
|/|Separator daty odpowiedni dla kultury.|Niedostępne.|  
|$|Symbol waluty właściwej dla kultury.|Niedostępne.|  
|\<|Konwertuje wszystkie znaki, które po znaku należy do małych liter.|Niedostępne.|  
|>|Konwertuje wszystkie znaki występujące po Wielkiej litery.|Niedostępne.|  
|&#124;|Cofa poprzednią zmianę lub przesunięcie w dół.|Niedostępne.|  
|&#92;|Wyprowadza znak maski, przełączając go do literału. " \\ \\ " jest sekwencją ucieczki dla ukośnika odwrotnego.|&#92;|  
|Wszystkie inne znaki.|Literały. Wszystkie elementy, które nie są maskami, będą wyświetlane w obrębie <xref:System.Windows.Forms.MaskedTextBox> .|Wszystkie inne znaki.|  
  
 Symbole dziesiętne (.), stutysięcznych (,), Time (:), Date (/) i Currency ($) są domyślne do wyświetlania tych symboli zgodnie z kulturą aplikacji. Można wymusić wyświetlanie symboli dla innej kultury przy użyciu <xref:System.Windows.Forms.MaskedTextBox.FormatProvider%2A> właściwości.  
  
## <a name="regular-expressions-and-masks"></a>Wyrażenia regularne i maski  
 Chociaż można używać wyrażeń regularnych i masek do sprawdzania poprawności danych wejściowych użytkownika, nie są one całkowicie równoważne. Wyrażenia regularne mogą wyrażać bardziej złożone wzorce niż maski, ale maski mogą bardziej zwięzłie wyrazić te same informacje i w istotnie odpowiednim formacie.  
  
 W poniższej tabeli porównano cztery wyrażenia regularne i równoważną maskę dla każdego z nich.  
  
|Wyrażenie regularne|Maska|Uwagi|  
|------------------------|----------|-----------|  
|`\d{2}/\d{2}/\d{4}`|`00/00/0000`|`/`Znak w masce jest logicznym separatorem daty i będzie widoczny dla użytkownika jako separator daty odpowiedni dla bieżącej kultury aplikacji.|  
|`\d{2}-[A-Z][a-z]{2}-\d{4}`|`00->L<LL-0000`|Data (dzień, skrót miesiąca i rok) w formacie Stany Zjednoczone, w którym skrót z trzema literami miesiąca jest wyświetlany z początkową wielką literą, a następnie dwoma małymi literami.|  
|`(\(\d{3}\)-)?\d{3}-d{4}`|`(999)-000-0000`|Stany Zjednoczone numer telefonu, kod obszaru opcjonalny. Jeśli użytkownik nie chce wprowadzać znaków opcjonalnych, może wprowadzić spacje lub umieścić wskaźnik myszy bezpośrednio na pozycji w masce reprezentowanej przez pierwsze 0.|  
|`$\d{6}.00`|`$999,999.00`|Wartość waluty z zakresu od 0 do 999999. Znaki Currency, thousandth i Decimal zostaną zastąpione w czasie wykonywania przy użyciu ich odpowiedników specyficznych dla kultury.|  
  
## <a name="see-also"></a>Zobacz też

- <xref:System.Windows.Forms.MaskedTextBox.Mask%2A>
- <xref:System.Windows.Forms.MaskedTextBox>
- [Sprawdzanie poprawności ciągów w Visual Basic](validating-strings.md)
- [MaskedTextBox, kontrolka](../../../../framework/winforms/controls/maskedtextbox-control-windows-forms.md)

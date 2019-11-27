---
title: Używanie wyrażeń regularnych z kontrolką MaskedTextBox
ms.date: 07/20/2015
helpviewer_keywords:
- strings [Visual Basic], regular expressions
- strings [Visual Basic], masked edit
ms.assetid: 2a048fb0-7053-487d-b2c5-ffa5e22ed6f9
ms.openlocfilehash: 12d500fa0ff4945dcf2d5009bdba6d337834707e
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/22/2019
ms.locfileid: "74346262"
---
# <a name="using-regular-expressions-with-the-maskedtextbox-control-in-visual-basic"></a>Używanie wyrażeń regularnych z formantem MaskedTextBox w Visual Basic
W tym przykładzie pokazano, jak konwertować proste wyrażenia regularne do pracy z kontrolką <xref:System.Windows.Forms.MaskedTextBox>.  
  
## <a name="description-of-the-masking-language"></a>Opis języka maskowania  
 Standardowy <xref:System.Windows.Forms.MaskedTextBox> język maskowania jest oparty na tym, kto jest używany przez kontrolkę `Masked Edit` w Visual Basic 6,0 i powinien być zaznajomiony z użytkownikami migrowaniem z tej platformy.  
  
 Właściwość <xref:System.Windows.Forms.MaskedTextBox.Mask%2A> kontrolki <xref:System.Windows.Forms.MaskedTextBox> określa maskę wprowadzania, która ma być używana. Maska musi być ciągiem składającym się z co najmniej jednego elementu maskowania z poniższej tabeli.  
  
|Maskowanie elementu|Opis|Element wyrażenia regularnego|  
|---------------------|-----------------|--------------------------------|  
|0|Dowolna pojedyncza cyfra z przedziału od 0 do 9. Wpis jest wymagany.|\d|  
|9|Cyfra lub spacja. Wpis opcjonalny.|[\d]?|  
|#|Cyfra lub spacja. Wpis opcjonalny. W przypadku pozostawienia pustej pozycji w masce zostanie ona renderowana jako spacja. Znaki plus (+) i minus (-) są dozwolone.|[ \d+-]?|  
|L|Litera ASCII. Wpis jest wymagany.|[a-zA-Z]|  
|?|Litera ASCII. Wpis opcjonalny.|[a-zA-Z]?|  
|&|Opis. Wpis jest wymagany.|[\p{Ll}\p{Lu}\p{Lt}\p{Lm}\p{Lo}]|  
|C|Opis. Wpis opcjonalny.|[\p{Ll}\p{Lu}\p{Lt}\p{Lm}\p{Lo}]?|  
|ELEMENT|Pełnej. Wpis opcjonalny.|\W|  
|.|Odpowiedni symbol zastępczy dziesiętnej kultury.|Niedostępne.|  
|,|Symbol zastępczy tysięcy odpowiednich kultur.|Niedostępne.|  
|:|Separator czasu odpowiedni dla kultury.|Niedostępne.|  
|/|Separator daty odpowiedni dla kultury.|Niedostępne.|  
|$|Symbol waluty właściwej dla kultury.|Niedostępne.|  
|\<|Konwertuje wszystkie znaki, które po znaku należy do małych liter.|Niedostępne.|  
|>|Konwertuje wszystkie znaki występujące po Wielkiej litery.|Niedostępne.|  
|&#124;|Cofa poprzednią zmianę lub przesunięcie w dół.|Niedostępne.|  
|&#92;|Wyprowadza znak maski, przełączając go do literału. "\\\\" to sekwencja ucieczki dla ukośnika odwrotnego.|&#92;|  
|Wszystkie inne znaki.|Literały. Wszystkie elementy niebędące maskami będą widoczne jako same w <xref:System.Windows.Forms.MaskedTextBox>.|Wszystkie inne znaki.|  
  
 Symbole dziesiętne (.), stutysięcznych (,), Time (:), Date (/) i Currency ($) są domyślne do wyświetlania tych symboli zgodnie z kulturą aplikacji. Można wymusić wyświetlanie symboli dla innej kultury przy użyciu właściwości <xref:System.Windows.Forms.MaskedTextBox.FormatProvider%2A>.  
  
## <a name="regular-expressions-and-masks"></a>Wyrażenia regularne i maski  
 Chociaż można używać wyrażeń regularnych i masek do sprawdzania poprawności danych wejściowych użytkownika, nie są one całkowicie równoważne. Wyrażenia regularne mogą wyrażać bardziej złożone wzorce niż maski, ale maski mogą bardziej zwięzłie wyrazić te same informacje i w istotnie odpowiednim formacie.  
  
 W poniższej tabeli porównano cztery wyrażenia regularne i równoważną maskę dla każdego z nich.  
  
|Wyrażenie regularne|Bitowa|Uwagi|  
|------------------------|----------|-----------|  
|`\d{2}/\d{2}/\d{4}`|`00/00/0000`|Znak `/` w masce jest logicznym separatorem daty i będzie widoczny dla użytkownika jako separator daty odpowiedni dla bieżącej kultury aplikacji.|  
|`\d{2}-[A-Z][a-z]{2}-\d{4}`|`00->L<LL-0000`|Data (dzień, skrót miesiąca i rok) w formacie Stany Zjednoczone, w którym skrót z trzema literami miesiąca jest wyświetlany z początkową wielką literą, a następnie dwoma małymi literami.|  
|`(\(\d{3}\)-)?\d{3}-d{4}`|`(999)-000-0000`|Stany Zjednoczone numer telefonu, kod obszaru opcjonalny. Jeśli użytkownik nie chce wprowadzać znaków opcjonalnych, może albo wprowadzić spacje, albo umieścić wskaźnik myszy bezpośrednio na pozycji w masce reprezentowanej przez pierwsze 0.|  
|`$\d{6}.00`|`$999,999.00`|Wartość waluty z zakresu od 0 do 999999. Znaki Currency, thousandth i Decimal zostaną zastąpione w czasie wykonywania przy użyciu ich odpowiedników specyficznych dla kultury.|  
  
## <a name="see-also"></a>Zobacz także

- <xref:System.Windows.Forms.MaskedTextBox.Mask%2A>
- <xref:System.Windows.Forms.MaskedTextBox>
- [Sprawdzanie poprawności ciągów w Visual Basic](../../../../visual-basic/programming-guide/language-features/strings/validating-strings.md)
- [MaskedTextBox, kontrolka](../../../../framework/winforms/controls/maskedtextbox-control-windows-forms.md)

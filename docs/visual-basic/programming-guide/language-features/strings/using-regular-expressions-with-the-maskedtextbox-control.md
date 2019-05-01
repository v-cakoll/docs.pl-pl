---
title: Używanie wyrażeń regularnych z formantem MaskedTextBox w Visual Basic
ms.date: 07/20/2015
helpviewer_keywords:
- strings [Visual Basic], regular expressions
- strings [Visual Basic], masked edit
ms.assetid: 2a048fb0-7053-487d-b2c5-ffa5e22ed6f9
ms.openlocfilehash: e0165fb8d573878ae19378b2656d89627680b804
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62024511"
---
# <a name="using-regular-expressions-with-the-maskedtextbox-control-in-visual-basic"></a>Używanie wyrażeń regularnych z formantem MaskedTextBox w Visual Basic
W tym przykładzie opisano sposób konwertowania proste wyrażenia regularnego do pracy z <xref:System.Windows.Forms.MaskedTextBox> kontroli.  
  
## <a name="description-of-the-masking-language"></a>Opis języka maskowania  
 Standardowa <xref:System.Windows.Forms.MaskedTextBox> maskowania języka opiera się na używaną przez `Masked Edit` kontrolowania w Visual Basic 6.0 i powinny być dobrze znanym użytkownikom migracji z tej platformy.  
  
 <xref:System.Windows.Forms.MaskedTextBox.Mask%2A> Właściwość <xref:System.Windows.Forms.MaskedTextBox> kontroli określa, jakie maska wprowadzania do użycia. Maska musi być ciąg, który składa się z co najmniej jeden z elementów maskowania z poniższej tabeli.  
  
|Element maskowania|Opis|Element wyrażenia regularnego|  
|---------------------|-----------------|--------------------------------|  
|0|Dowolna cyfra od 0 do 9. Należy wypełnić.|\d|  
|9|Cyfra lub spacja. Pozycja opcjonalna.|[ \d]?|  
|#|Cyfra lub spacja. Pozycja opcjonalna. Jeśli ta pozycja jest puste w masce, będzie ona renderowana jako spacja. Plus (+) oraz minus (-) znaki są dozwolone.|[ \d+-]?|  
|L|Litery ASCII. Należy wypełnić.|[a-zA-Z]|  
|?|Litery ASCII. Pozycja opcjonalna.|[a-zA-Z]?|  
|&|znak. Należy wypełnić.|[\p{Ll}\p{Lu}\p{Lt}\p{Lm}\p{Lo}]|  
|C|znak. Pozycja opcjonalna.|[\p{Ll}\p{Lu}\p{Lt}\p{Lm}\p{Lo}]?|  
|ELEMENT|Alfanumeryczne. Pozycja opcjonalna.|\W|  
|.|Odpowiedni kulturowo dziesiętna symbol zastępczy.|Nie jest dostępna.|  
|,|Symbol zastępczy tysięcy odpowiedni kulturowo.|Nie jest dostępna.|  
|:|Separator godziny odpowiedni kulturowo.|Nie jest dostępna.|  
|/|Separator daty odpowiedni kulturowo.|Nie jest dostępna.|  
|$|Symbol waluty odpowiedni kulturowo.|Nie jest dostępna.|  
|\<|Konwertuje wszystkie znaki, które należy wykonać na małe litery.|Nie jest dostępna.|  
|>|Konwertuje wszystkie znaki, które należy wykonać na wielkie litery.|Nie jest dostępna.|  
|&#124;|Cofa poprzedniej zmiany w górę lub w dół.|Nie jest dostępna.|  
|&#92;|Zmienia znaczenie znaku maska, włączając je na literał. "\\\\" sekwencję ucieczki dla ukośnik odwrotny.|&#92;|  
|Wszystkie inne znaki.|Literały. Wszystkie elementy maska nie będą wyświetlane jako siebie w ramach <xref:System.Windows.Forms.MaskedTextBox>.|Wszystkie inne znaki.|  
  
 Dziesiętnego (.), tysięczne (,), czas (:), Data (/) i domyślne symbole określający walutę ($) do wyświetlania tych symboli, zgodnie z definicją kultury aplikacji. Można wymusić na nich w celu wyświetlenia symboli dla kultury innej przy użyciu <xref:System.Windows.Forms.MaskedTextBox.FormatProvider%2A> właściwości.  
  
## <a name="regular-expressions-and-masks"></a>Wyrażenia regularne i masek  
 Chociaż można używać wyrażeń regularnych i masek, aby sprawdzić poprawność danych wejściowych użytkownika, nie są całkowicie równoważne. Wyrażeń regularnych można wyrazić wzorców bardziej skomplikowane niż masek, ale maski można wyrazić te same informacje, bardziej zwięzły i kulturalnie odpowiedni format.  
  
 W poniższej tabeli porównano cztery wyrażeń regularnych i równoważne maski dla każdego.  
  
|Wyrażenie regularne|Maska|Uwagi|  
|------------------------|----------|-----------|  
|`\d{2}/\d{2}/\d{4}`|`00/00/0000`|`/` Znak maski jest separator daty logicznych i będzie ono wyświetlane użytkownikowi jako separator daty odpowiednie dla bieżącej kultury aplikacji.|  
|`\d{2}-[A-Z][a-z]{2}-\d{4}`|`00->L<LL-0000`|Data (dzień, skrót miesiąca i roku) w formacie Stanów Zjednoczonych, w którym miesiącu trzyliterowy skrót jest wyświetlany z początkową wielką literą, następuje dwa małe litery.|  
|`(\(\d{3}\)-)?\d{3}-d{4}`|`(999)-000-0000`|Numer telefonu Stanów Zjednoczonych, numer kierunkowy opcjonalne. Jeśli użytkownik nie chce wprowadzić znaki opcjonalne, ona wprowadź miejsca do magazynowania lub umieść wskaźnik myszy bezpośrednio w położeniu maski reprezentowany przez pierwsze 0.|  
|`$\d{6}.00`|`$999,999.00`|Wartość waluty z zakresu od 0 do 999 999. Waluty, tysięczną i znaki dziesiętne zostaną zastąpione w czasie wykonywania za pomocą ich odpowiedników specyficzne dla kultury.|  
  
## <a name="see-also"></a>Zobacz także

- <xref:System.Windows.Forms.MaskedTextBox.Mask%2A>
- <xref:System.Windows.Forms.MaskedTextBox>
- [Sprawdzanie poprawności ciągów w Visual Basic](../../../../visual-basic/programming-guide/language-features/strings/validating-strings.md)
- [MaskedTextBox, kontrolka](../../../../framework/winforms/controls/maskedtextbox-control-windows-forms.md)

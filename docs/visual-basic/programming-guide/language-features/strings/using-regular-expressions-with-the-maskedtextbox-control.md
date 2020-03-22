---
title: Używanie wyrażeń regularnych z kontrolką MaskedTextBox
ms.date: 07/20/2015
helpviewer_keywords:
- strings [Visual Basic], regular expressions
- strings [Visual Basic], masked edit
ms.assetid: 2a048fb0-7053-487d-b2c5-ffa5e22ed6f9
ms.openlocfilehash: b997f6f495fca51e888bb995fee0361d29d68048
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/12/2020
ms.locfileid: "79148287"
---
# <a name="using-regular-expressions-with-the-maskedtextbox-control-in-visual-basic"></a>Używanie wyrażeń regularnych z formantem MaskedTextBox w Visual Basic
W tym przykładzie pokazano, jak konwertować <xref:System.Windows.Forms.MaskedTextBox> proste wyrażenia regularne do pracy z formantem.  
  
## <a name="description-of-the-masking-language"></a>Opis języka maskującego  
 Standardowy <xref:System.Windows.Forms.MaskedTextBox> język maskowania jest oparty na `Masked Edit` języku używanym przez formant w języku Visual Basic 6.0 i powinien być znany użytkownikom migrującymi z tej platformy.  
  
 Właściwość <xref:System.Windows.Forms.MaskedTextBox.Mask%2A> <xref:System.Windows.Forms.MaskedTextBox> formantu określa, jakiej maski wejściowej użyć. Maska musi być ciągiem składającym się z jednego lub więcej elementów maskujących z poniższej tabeli.  
  
|Element maskujący|Opis|Element wyrażenia regularnego|  
|---------------------|-----------------|--------------------------------|  
|0|Dowolna pojedyncza cyfra od 0 do 9. Wymagane wpisy.|\d|  
|9|Cyfra lub spacja. Wpis opcjonalny.|[ \d]?|  
|#|Cyfra lub spacja. Wpis opcjonalny. Jeśli ta pozycja pozostanie pusta w masce, zostanie renderowana jako spacja. Dozwolone są znaki plus (+) i minus (-).|[ \d+-]?|  
|L|list ASCII. Wymagane wpisy.|[a-zA-Z]|  
|?|list ASCII. Wpis opcjonalny.|[a-zA-Z]?|  
|&|Znaków. Wymagane wpisy.|[\p{Ll}\p{Lu}\p{Lt}\p{Lm}\p{Lo}]|  
|C|Znaków. Wpis opcjonalny.|[\p{Ll}\p{Lu}\p{Lt}\p{Lm}\p{Lo}]?|  
|A|Alfanumerycznych. Wpis opcjonalny.|\W|  
|.|Symbol zastępczy z odpowiednimi kulturami dziesiętnymi.|Niedostępne.|  
|,|Kultury odpowiednie tysiące symbol zastępczy.|Niedostępne.|  
|:|Separator czasu odpowiedni dla kultury.|Niedostępne.|  
|/|Separator daty odpowiedni dla kultury.|Niedostępne.|  
|$|Symbol waluty odpowiedni dla kultury.|Niedostępne.|  
|\<|Konwertuje wszystkie znaki, które następują po małych literach.|Niedostępne.|  
|>|Konwertuje wszystkie znaki, które następują po nim, na wielkie litery.|Niedostępne.|  
|&#124;|Cofa poprzednią zmianę w górę lub przesuń w dół.|Niedostępne.|  
|&#92;|Ucieka znak maski, zamieniając go w dosłowny. "\\\\" to sekwencja ucieczki dla ukośnika odwrotnego.|&#92;|  
|Wszystkie inne znaki.|Literały. Wszystkie elementy niemagazysowe <xref:System.Windows.Forms.MaskedTextBox>pojawią się same w obrębie .|Wszystkie inne znaki.|  
  
 Symbole dziesiętne (.), tysięczni (,), czas (:), data (/) i waluta ($) domyślnie wyświetlają te symbole zgodnie z definicją kultury aplikacji. Można wymusić ich do wyświetlania symboli <xref:System.Windows.Forms.MaskedTextBox.FormatProvider%2A> dla innej kultury przy użyciu właściwości.  
  
## <a name="regular-expressions-and-masks"></a>Wyrażenia regularne i maski  
 Chociaż można użyć wyrażeń regularnych i masek do sprawdzania poprawności danych wejściowych użytkownika, nie są one całkowicie równoważne. Wyrażenia regularne mogą wyrażać bardziej złożone wzorce niż maski, ale maski mogą wyrażać te same informacje bardziej zwięźle i w formacie odpowiednim kulturowo.  
  
 W poniższej tabeli porównano cztery wyrażenia regularne i równoważną maskę dla każdego z nich.  
  
|Wyrażenie regularne|Maska|Uwagi|  
|------------------------|----------|-----------|  
|`\d{2}/\d{2}/\d{4}`|`00/00/0000`|Znak `/` w masce jest logicznym separatorem daty i pojawi się dla użytkownika jako separator daty odpowiedni dla bieżącej kultury aplikacji.|  
|`\d{2}-[A-Z][a-z]{2}-\d{4}`|`00->L<LL-0000`|Data (dzień, skrót miesiąca i rok) w formacie Stanów Zjednoczonych, w której trzyliterowy skrót miesiąca jest wyświetlany z początkową wielką literą, po której następują dwie małe litery.|  
|`(\(\d{3}\)-)?\d{3}-d{4}`|`(999)-000-0000`|Numer telefonu w Stanach Zjednoczonych, numer kierunkowy opcjonalny. Jeśli użytkownik nie chce wprowadzić znaków opcjonalnych, może wprowadzić spacje lub umieścić wskaźnik myszy bezpośrednio w miejscu w masce reprezentowane przez pierwsze 0.|  
|`$\d{6}.00`|`$999,999.00`|Wartość waluty w zakresie od 0 do 999999. Znaki waluty, tysięczna i dziesiętna zostaną zastąpione w czasie wykonywania ich odpowiednikami specyficznymi dla kultury.|  
  
## <a name="see-also"></a>Zobacz też

- <xref:System.Windows.Forms.MaskedTextBox.Mask%2A>
- <xref:System.Windows.Forms.MaskedTextBox>
- [Sprawdzanie poprawności ciągów w Visual Basic](../../../../visual-basic/programming-guide/language-features/strings/validating-strings.md)
- [MaskedTextBox, kontrolka](../../../../framework/winforms/controls/maskedtextbox-control-windows-forms.md)

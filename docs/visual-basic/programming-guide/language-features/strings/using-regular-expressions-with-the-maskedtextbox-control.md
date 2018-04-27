---
title: Używanie wyrażeń regularnych z formantem MaskedTextBox w Visual Basic
ms.custom: ''
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: ''
ms.suite: ''
ms.technology:
- devlang-visual-basic
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- strings [Visual Basic], regular expressions
- strings [Visual Basic], masked edit
ms.assetid: 2a048fb0-7053-487d-b2c5-ffa5e22ed6f9
caps.latest.revision: 10
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: c72542c05123ef62a8f95afbe1bb19cb823d1f21
ms.sourcegitcommit: 86adcc06e35390f13c1e372c36d2e044f1fc31ef
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/26/2018
---
# <a name="using-regular-expressions-with-the-maskedtextbox-control-in-visual-basic"></a>Używanie wyrażeń regularnych z formantem MaskedTextBox w Visual Basic
W tym przykładzie pokazano, jak przekonwertować prostych wyrażeń regularnych do pracy z <xref:System.Windows.Forms.MaskedTextBox> formantu.  
  
## <a name="description-of-the-masking-language"></a>Opis języka maskowania  
 Standardowe <xref:System.Windows.Forms.MaskedTextBox> maskowania języka jest oparta na używany przez `Masked Edit` kontroli w Visual Basic 6.0 i należy znać użytkownikom migrację z tej platformy.  
  
 <xref:System.Windows.Forms.MaskedTextBox.Mask%2A> Właściwość <xref:System.Windows.Forms.MaskedTextBox> kontroli określa, jakie maska wprowadzania do użycia. Maska musi być ciągiem składa się z co najmniej jeden z elementów maskowania z poniższej tabeli.  
  
|Element maskowania|Opis|Element wyrażeń regularnych|  
|---------------------|-----------------|--------------------------------|  
|0|Pojedynczej cyfry od 0 do 9. Wpis jest wymagany.|\d|  
|9|Cyfra lub spacja. Pozycja opcjonalna.|[\d]?|  
|#|Cyfra lub spacja. Pozycja opcjonalna. Jeśli ta pozycja jest puste maski, ma być odwzorowany jako spacją. Plus (+) oraz minus (-) można używać znaków.|[\d+-]?|  
|L|Litery ASCII. Wpis jest wymagany.|[a-zA-Z]|  
|?|Litery ASCII. Pozycja opcjonalna.|[a-zA-Z]?|  
|&|Znak. Wpis jest wymagany.|[\p{Ll}\p{Lu}\p{Lt}\p{Lm}\p{Lo}]|  
|C|Znak. Pozycja opcjonalna.|[\p{Ll}\p{Lu}\p{Lt}\p{Lm}\p{Lo}]?|  
|ELEMENT|Alfanumeryczne. Pozycja opcjonalna.|\W|  
|.|Odpowiednie kultury dziesiętny symbol zastępczy.|Nie jest dostępna.|  
|,|Symbol zastępczy tysięcy odpowiednie kultury.|Nie jest dostępna.|  
|:|Separator godziny odpowiednie kultury.|Nie jest dostępna.|  
|/|Separator daty odpowiednie kultury.|Nie jest dostępna.|  
|$|Symbol waluty odpowiednie kultury.|Nie jest dostępna.|  
|\<|Konwertuje wszystkie znaki, które należy wykonać na małe litery.|Nie jest dostępna.|  
|>|Konwertuje wszystkie znaki, które należy wykonać na wielkie litery.|Nie jest dostępna.|  
|&#124;|Cofa poprzedniej zmiany w górę lub w dół.|Nie jest dostępna.|  
|\|Specjalne znak maski, włączając w literału. "\\\\" sekwencję ucieczki dla ukośnik odwrotny.|\|  
|Wszystkie inne znaki.|Literały. Wszystkie elementy-mask pojawi się w <xref:System.Windows.Forms.MaskedTextBox>.|Wszystkie inne znaki.|  
  
 Decimal (.), tysięczne (,), czas (:), Data (/) i domyślne symbole waluty ($) do wyświetlania tych symboli, zgodnie z definicją kultury aplikacji. Można wymusić na nich w celu wyświetlenia symboli dla kultury innego przy użyciu <xref:System.Windows.Forms.MaskedTextBox.FormatProvider%2A> właściwości.  
  
## <a name="regular-expressions-and-masks"></a>Wyrażenia regularne i masek  
 Wyrażenia regularne i masek służy do sprawdzania poprawności danych wejściowych użytkownika, nie są one całkowicie równoważne. Wyrażenia regularne można wyrazić wzorce bardziej złożone niż maski, ale maski można wyrazić tych samych informacji więcej krótkiej formie i kulturalnie odpowiedni format.  
  
 W poniższej tabeli porównano cztery wyrażeń regularnych i maska równoważne dla każdego.  
  
|Wyrażenie regularne|Maska|Uwagi|  
|------------------------|----------|-----------|  
|`\d{2}/\d{2}/\d{4}`|`00/00/0000`|`/` Znak maski jest separatora operatory i będzie ono wyświetlane użytkownikowi jako separator daty odpowiednią dla bieżącej kultury aplikacji.|  
|`\d{2}-[A-Z][a-z]{2}-\d{4}`|`00->L<LL-0000`|Data (dzień, skrót miesiąca i roku) w formacie Stanów Zjednoczonych, w którym skrót miesiąca trzyliterowy zostanie wyświetlony z początkowej wielką literę, a następnie dwa małe litery.|  
|`(\(\d{3}\)-)?\d{3}-d{4}`|`(999)-000-0000`|Numer telefonu Stanów Zjednoczonych, numer kierunkowy opcjonalne. Jeśli użytkownik nie życzy sobie wprowadź znaki opcjonalne, klika wprowadź spacji lub umieść wskaźnik myszy bezpośrednio w pozycji w masce reprezentowany przez pierwszy 0.|  
|`$\d{6}.00`|`$999,999.00`|Wartość waluty w zakresie od 0 do 999999. Waluty, / 1000 i znaki dziesiętne zostaną zastąpione w czasie wykonywania ich odpowiedniki specyficzne dla kultury.|  
  
## <a name="see-also"></a>Zobacz też  
 <xref:System.Windows.Forms.MaskedTextBox.Mask%2A>  
 <xref:System.Windows.Forms.MaskedTextBox>  
 [Sprawdzanie poprawności ciągów w Visual Basic](../../../../visual-basic/programming-guide/language-features/strings/validating-strings.md)  
 [MaskedTextBox, kontrolka](../../../../framework/winforms/controls/maskedtextbox-control-windows-forms.md)

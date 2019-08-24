---
title: Błędy czasu projektowania w narzędziu Projektant dla formularzy systemu Windows
ms.date: 03/30/2017
f1_keywords:
- DTELErrorList
- WhyDTELPage
helpviewer_keywords:
- errors [Windows Forms Designer]
- design-time errors [Windows Forms Designer]
ms.assetid: ad408380-825a-46d8-9a4a-531b130b88ce
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: cce9baf1523391e281593428b633c401103b42b5
ms.sourcegitcommit: 121ab70c1ebedba41d276e436dd2b1502748a49f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/24/2019
ms.locfileid: "70015971"
---
# <a name="design-time-errors-in-the-windows-forms-designer"></a>Błędy czasu projektowania w Projektant formularzy systemu Windows

W tym temacie wyjaśniono znaczenie i użycie listy błędów czasu projektowania, która pojawia się w programie Visual Studio w przypadku niepowodzenia załadowania Projektant formularzy systemu Windows. Jeśli zostanie wyświetlona lista błędów, nie należy interpretować jej jako usterki w projektancie, ale jako pomoc w rozwiązywaniu błędów w kodzie.

Podstawowe informacje o tej liście błędów ułatwią debugowanie aplikacji przez podanie szczegółowych informacji o błędach i sugerowanie możliwych rozwiązań.

## <a name="the-design-time-error-list-interface"></a>Interfejs listy błędów czasu projektowania

Jeśli nie można załadować Projektant formularzy systemu Windows, w projektancie pojawi się lista błędów. Błędy są pogrupowane w kategorie. Na przykład jeśli masz cztery wystąpienia niezadeklarowanych zmiennych, zostaną one pogrupowane w tej samej kategorii błędów. Każda kategoria błędów zawiera krótki opis podsumowujący błąd.

Kategorię błędów można rozwinąć lub zwinąć, klikając nagłówek kategorii błędów lub klikając przycisk Rozwiń/Zwiń Pagon. Po rozwinięciu kategorii błędów zostanie wyświetlona następująca dodatkowa pomoc:

- Wystąpienia tego błędu.

- Pomoc dotycząca tego błędu.

- Wpisy na forum dotyczące tego błędu.

### <a name="instances-of-this-error"></a>Wystąpienia tego błędu

Dodatkowa pomoc dla wszystkich wystąpień błędu w bieżącym projekcie. Wiele błędów zawiera dokładną lokalizację w następującym formacie: *[nazwa projektu]* *[nazwa formularza]* wiersz: *[numer wiersza]* kolumna: *[numer kolumny]* . Link **Przejdź do kodu** przenosi do lokalizacji w kodzie, w której występuje błąd.

Jeśli stos wywołań jest skojarzony z błędem, można kliknąć link **Pokaż stos wywołań** , który dodatkowo rozszerza błąd w celu wyświetlenia stosu wywołań. Badanie stosu może zapewnić cenne informacje debugowania. Można na przykład śledzić funkcje, które zostały wywołane przed wystąpieniem błędu. Stos wywołań jest wybierany, aby można go było skopiować i zapisać.

> [!NOTE]
> W Visual Basic Lista błędów czasu projektowania nie wyświetla więcej niż jednego błędu, ale może wyświetlić wiele wystąpień tego samego błędu. W wizualizacji C++błędy nie mają linków do kodu linków/numerów wierszy.

### <a name="forum-posts-about-this-error"></a>Wpisy na forum dotyczące tego błędu

Dodatkowa pomoc zawiera link do wpisów na forum związanych z błędem. Fora są przeszukiwane w oparciu o ciąg komunikatu o błędzie. Możesz również spróbować wyszukać na następujących forach:

- [Forum Projektant formularzy systemu Windows](https://social.msdn.microsoft.com/Forums/windows/home?forum=winformsdesigner)

- [Forum Windows Forms](https://social.msdn.microsoft.com/Forums/windows/home?category=windowsforms)

### <a name="ignore-and-continue"></a>Ignoruj i Kontynuuj

Można zignorować warunek błędu i kontynuować ładowanie projektanta. Wybranie tej akcji może spowodować nieoczekiwane zachowanie. Na przykład kontrolki mogą nie być wyświetlane na powierzchni projektowej.

## <a name="see-also"></a>Zobacz także

- [Rozwiązywanie problemów związanych z projektowaniem czasu projektowania](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2013/ms171843(v=vs.120))
- [Rozwiązywanie problemów związanych z kontrolkami oraz tworzeniem składników](troubleshooting-control-and-component-authoring.md)
- [Opracowywanie kontrolek formularzy Windows Forms w czasie projektowania](developing-windows-forms-controls-at-design-time.md)
- [Projektant formularzy systemu Windows komunikaty o błędach](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/ms233640(v=vs.100))

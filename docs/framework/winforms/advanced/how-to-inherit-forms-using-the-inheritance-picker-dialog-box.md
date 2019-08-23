---
title: 'Instrukcje: Dziedziczenie formularzy korzystających z okna dialogowego selektora dziedziczenia'
ms.date: 03/30/2017
helpviewer_keywords:
- inheritance [Windows Forms], forms
- Inheritance Picker dialog box
- inherited forms [Windows Forms], creating
ms.assetid: 969b4c04-12aa-4297-93a2-0ae747447823
ms.openlocfilehash: 6fdd1e72e4256db30d9fb6a3b560c3d538435c79
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2019
ms.locfileid: "69931880"
---
# <a name="how-to-inherit-forms-using-the-inheritance-picker"></a>Instrukcje: Dziedzicz formularze przy użyciu selektora dziedziczenia

Najprostszym sposobem na dziedziczenie formularza lub innego obiektu jest użycie okna dialogowego **selektora dziedziczenia** . Dzięki niej można korzystać z interfejsów kodu lub użytkownika (UI), które zostały już utworzone w innych rozwiązaniach.

> [!NOTE]
> Aby można było dziedziczyć z formularza przy użyciu okna dialogowego selektora dziedziczenia, projekt zawierający ten formularz musi być wbudowany w plik wykonywalny lub dll. Aby skompilować projekt, wybierz opcję **Kompiluj rozwiązanie** z menu **kompilacja** .

## <a name="create-a-windows-form-by-using-the-inheritance-picker"></a>Tworzenie formularza systemu Windows przy użyciu selektora dziedziczenia

1. W programie Visual Studio w menu **projekt** wybierz polecenie **Dodaj formularz systemu Windows**.

   **Dodaj nowy element** zostanie otwarte okno dialogowe.

2. Przeszukaj **Dziedziczony szablon formularza** z SearchBox lub klikając kategorię **Windows Forms** , zaznacz ją i nadaj jej nazwę w polu **Nazwa** . Kliknij przycisk **Dodaj** , aby rozpocząć.

   Zostanie otwarte okno dialogowe **Selektor dziedziczenia** . Jeśli bieżący projekt zawiera już formularze, są one wyświetlane w oknie dialogowym **Selektor dziedziczenia** .

3. Aby dziedziczyć z formularza w innym zestawie, kliknij przycisk **Przeglądaj** .

4. W oknie dialogowym **Wybierz plik, który zawiera składnik do dziedziczenia z** , przejdź do projektu zawierającego żądany formularz lub moduł.

5. Kliknij nazwę pliku. exe lub. dll, aby go zaznaczyć, a następnie kliknij przycisk **Otwórz** .

   Spowoduje to powrót do okna dialogowego selektora dziedziczenia, gdzie składnik jest teraz wymieniony, wraz z projektem, w którym się znajduje.

6. Wybierz składnik.

   W **Eksplorator rozwiązań**składnik jest dodawany do projektu. Jeśli ma interfejs użytkownika, formanty, które są częścią dziedziczonego formularza, będą oznaczone symbolem (![zrzut ekranu przedstawiający](./media/how-to-inherit-forms-using-the-inheritance-picker-dialog-box/visual-basic-inheritance-glyph.gif)symbol dziedziczenia Visual Basic), i, po wybraniu, mają obramowanie wskazujące poziom zabezpieczeń, który formant ma na podformularz z klasą. Zachowania zgodne z różnymi poziomami zabezpieczeń są wymienione w poniższej tabeli.

    |Poziom zabezpieczeń kontroli|Interakcja dostępna za pomocą projektanta i edytora kodu z dziedziczonym formularzem|
    |-------------------------------|--------------------------------------------------------------------------------|
    |Public|Obramowanie standardowe z uchwytami zmiany rozmiaru: formant może mieć rozmiar i przesunięty. Dostęp do formantu można wykonać wewnętrznie przez klasę, która deklaruje ją i zewnętrznie przez inne klasy.|
    |Protected|Obramowanie standardowe z uchwytami zmiany rozmiaru: formant może mieć rozmiar i przesunięty. Mogą być dostępne wewnętrznie przez klasę, która deklaruje ją i każdej klasy, która dziedziczy z klasy nadrzędnej, ale nie może uzyskać do niej dostępu przy użyciu klas zewnętrznych.|
    |Chroniona wewnętrznie (chroniona osoba zaprzyjaźniona w Visual Basic)|Obramowanie standardowe z uchwytami zmiany rozmiaru: formant może mieć rozmiar i przesunięty. Mogą być dostępne wewnętrznie przez klasę, która deklaruje ją, przez dowolną klasę, która dziedziczy z klasy nadrzędnej, i przez innych członków zestawu, który go zawiera.|
    |Wewnętrzny (Friend w Visual Basic)|Obramowanie standardowe bez dojścia do rozmiarów, wyświetlane w formularzu, właściwości widoczne w oknie **Właściwości** . Jednak wszystkie aspekty kontrolki będą traktowane jako tylko do odczytu. Nie można przenieść ani zmienić rozmiaru kontrolki ani zmieniać jej właściwości. Jeśli formant jest kontenerem innych kontrolek, takich jak pole grupy, nie można dodać nowych kontrolek i nie można usunąć istniejących kontrolek, nawet jeśli te kontrolki były publiczne. Dostęp do formantu można uzyskać tylko przez innych członków zestawu, który go zawiera.|
    |Private|Obramowanie standardowe bez dojścia do rozmiarów, wyświetlane w formularzu, właściwości widoczne w oknie **Właściwości** . Jednak wszystkie aspekty kontrolki będą traktowane jako tylko do odczytu. Nie można przenieść ani zmienić rozmiaru kontrolki ani zmieniać jej właściwości. Jeśli formant jest kontenerem innych kontrolek, takich jak pole grupy, nie można dodać nowych kontrolek i nie można usunąć istniejących kontrolek, nawet jeśli te kontrolki były publiczne. Dostęp do formantu można uzyskać tylko przez klasę, która ją deklaruje.|

     Aby dowiedzieć się, jak zmienić wygląd formularza podstawowego, zobacz [skutki modyfikacji wyglądu formularza podstawowego](effects-of-modifying-base-form-appearance.md).

    > [!NOTE]
    > Po połączeniu dziedziczonych kontrolek i składników ze standardowymi kontrolkami i składnikami na Windows Forms mogą wystąpić konflikty z kolejnością z. Można to poprawić, modyfikując porządek osi z, klikając w menu **Format** , wskazując polecenie **kolejność**, a następnie klikając polecenie **Przesuń na wierzch** lub **Przesuń na spód**. Aby uzyskać więcej informacji na temat porządku osi z kontrolek, [zobacz How to: Obiekty warstwy na Windows Forms](../controls/how-to-layer-objects-on-windows-forms.md).

## <a name="see-also"></a>Zobacz także

- [Inherits, instrukcja](../../../visual-basic/language-reference/statements/inherits-statement.md)
- [using](../../../csharp/language-reference/keywords/using.md)
- [Efekty modyfikowania wyglądu formularza podstawowego](effects-of-modifying-base-form-appearance.md)
- [Formularze Windows Forms — dziedziczenie wizualizacji](windows-forms-visual-inheritance.md)

---
title: 'Instrukcje: Dziedziczenie formularzy korzystających z okna dialogowego selektora dziedziczenia'
ms.date: 03/30/2017
helpviewer_keywords:
- inheritance [Windows Forms], forms
- Inheritance Picker dialog box
- inherited forms [Windows Forms], creating
ms.assetid: 969b4c04-12aa-4297-93a2-0ae747447823
ms.openlocfilehash: 5ae1c236835141b10bc704cd39f55de6e3e974b0
ms.sourcegitcommit: 558d78d2a68acd4c95ef23231c8b4e4c7bac3902
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/09/2019
ms.locfileid: "59342096"
---
# <a name="how-to-inherit-forms-using-the-inheritance-picker-dialog-box"></a>Instrukcje: Dziedziczenie formularzy korzystających z okna dialogowego selektora dziedziczenia
Najprostszym sposobem dziedziczą formularza lub inny obiekt jest użycie **selektor dziedziczenia** okno dialogowe. Dzięki niemu można korzystać z zalet interfejsów kodu lub użytkownika (UI), utworzono już w innych rozwiązaniach.  
  
> [!NOTE]
>  Aby dziedziczyć z formularza z **selektor dziedziczenia** okno dialogowe do projektu zawierającego ten formularz musi zostały skompilowane do pliku wykonywalnego lub biblioteki DLL. Aby skompilować projekt, wybierz opcję **Kompiluj rozwiązanie** z **kompilacji** menu.  
>   
>  Okna dialogowe i polecenia menu mogą się różnić od tych opisanych w Pomocy, w zależności od ustawień aktywnych lub wydania. Aby zmienić swoje ustawienia, wybierz opcję **Import i eksport ustawień** na **narzędzia** menu. Aby uzyskać więcej informacji, zobacz [personalizowanie środowiska IDE programu Visual Studio](/visualstudio/ide/personalizing-the-visual-studio-ide).  
  
### <a name="to-create-a-windows-form-inherited-from-an-existing-form-by-using-the-inheritance-picker"></a>Aby utworzyć formularz Windows dziedziczone z istniejącego formularza za pomocą selektora dziedziczenia  
  
1. Z **projektu** menu, wybierz **Dodaj formularz Windows**.  
  
     **Dodaj nowy element** zostanie otwarte okno dialogowe.  
  
2. Wyszukiwanie **dziedziczone formularza** szablonu z searchbox lub klikając **formularzy Windows** kategorii, zaznacz ją, a następnie nadaj mu w **nazwa** pole. Kliknij przycisk **Dodaj** przycisk, aby kontynuować.  
  
     **Selektor dziedziczenia** zostanie otwarte okno dialogowe. Jeśli bieżący projekt zawiera już formularzy, zostaną one wyświetlone w **selektor dziedziczenia** okno dialogowe.  
  
3. Dziedziczenie z formularza w innym zestawie, kliknij przycisk **Przeglądaj** przycisku.  
  
4. W ramach **wybierz plik, który zawiera składnik do dziedziczenia** okno dialogowe, przejdź do projektu zawierającego formularz lub moduł wygodną pracę.  
  
5. Kliknij nazwę pliku .exe lub .dll, aby go zaznaczyć, a następnie kliknij przycisk **Otwórz** przycisku.  
  
     Nastąpi powrót do **selektor dziedziczenia** okno dialogowe, w którym składnik znajduje się teraz, wraz z projektu, w którym znajduje się.  
  
6. Wybierz składnik.  
  
     W **Eksploratora rozwiązań**, składnik zostanie dodany do projektu. Ma interfejs użytkownika, kontrolek, które są częścią odziedziczony formularz będą oznaczone znakiem glif (![zrzut ekranu przedstawiający symboli dziedziczenie Visual Basic.](./media/how-to-inherit-forms-using-the-inheritance-picker-dialog-box/visual-basic-inheritance-glyph.gif)), a po wybraniu miała obramowanie wskazujący poziom zabezpieczeń, między formantem podklasy formularz. W poniższej tabeli wymieniono zachowań, które odnoszą się do różnych poziomów ochrony.  
  
    |Poziom kontroli zabezpieczeń|Dostępne interakcji za pomocą projektanta i edytora kodu za pomocą formularza dziedziczone|  
    |-------------------------------|--------------------------------------------------------------------------------|  
    |Public|Standardowa obramowanie z uchwytami zmiany rozmiaru: może być o rozmiarze i przenieść kontroli. Formant może zostać oceniony wewnętrznie przez klasę, która deklaruje ją i zewnętrznie innych klas.|  
    |Protected|Standardowa obramowanie z uchwytami zmiany rozmiaru: może być o rozmiarze i przenieść kontroli. Możliwy wewnętrznie przez klasę, która deklaruje ją i każdej klasy, która dziedziczy z klasy nadrzędnej, ale nie są dostępne przez zewnętrzne klasy.|  
    |Chronionych wewnętrznych (chronionych Friend w języku Visual Basic)|Standardowa obramowanie z uchwytami zmiany rozmiaru: może być o rozmiarze i przenieść kontroli. Może zostać oceniony wewnętrznie przez klasę, która deklaruje ją, dowolnej klasy dziedziczącej z klasy nadrzędnej i inni członkowie zestawu, który go zawiera.|  
    |Wewnętrzny (Friend w języku Visual Basic)|Standardowa obramowanie z nie uchwyty zmiany rozmiaru, wyświetlane w formularzu właściwości widocznych w **właściwości** okna. Jednak wszystkie aspekty kontrolki będą uznawane za tylko do odczytu. Nie można przenieść lub rozmiar kontrolki lub zmienić jego właściwości. Jeśli kontrolka jest kontenerem inne formanty, takie jak pola grupy nie można dodać nowych kontrolek i nie można usunąć istniejące kontrolki, nawet jeśli te kontrolki były publiczne. Formant może zostać oceniony jedynie przez innych członków zestawu, który go zawiera.|  
    |Private|Standardowa obramowanie z nie uchwyty zmiany rozmiaru, wyświetlane w formularzu właściwości widocznych w **właściwości** okna. Jednak wszystkie aspekty kontrolki będą uznawane za tylko do odczytu. Nie można przenieść lub rozmiar kontrolki lub zmienić jego właściwości. Jeśli kontrolka jest kontenerem inne formanty, takie jak pola grupy nie można dodać nowych kontrolek i nie można usunąć istniejące kontrolki, nawet jeśli te kontrolki były publiczne. Formant może zostać oceniony jedynie przez klasę, która deklaruje ją.|  
  
     Aby uzyskać informacje o tym, jak zmienić wygląd formularza podstawowego, zobacz [efekty modyfikowania wyglądu formularza podstawowego](effects-of-modifying-base-form-appearance.md).  
  
    > [!NOTE]
    >  Łącząc dziedziczone kontrolek i składników za pomocą standardowych kontrolek i składników na formularzach Windows Forms, może wystąpić powoduje konflikt z kolejności z. Problem można rozwiązać, zmieniając porządku osi z, które jest realizowane przez kliknięcie w **Format** menu, wskazać polecenie **kolejności**, a następnie klikając polecenie **Przesuń na wierzch** lub  **Przesuń na spód**. Aby uzyskać więcej informacji na temat kolejności z formantów zobacz [jak: Warstw obiektów na formularzach Windows Forms](../controls/how-to-layer-objects-on-windows-forms.md).  
  
## <a name="see-also"></a>Zobacz także

- [Inherits — Instrukcja](~/docs/visual-basic/language-reference/statements/inherits-statement.md)
- [korzystanie](~/docs/csharp/language-reference/keywords/using.md)
- [Efekty modyfikowania wyglądu formularza podstawowego](effects-of-modifying-base-form-appearance.md)
- [Formularze systemu Windows — dziedziczenie Visual](windows-forms-visual-inheritance.md)

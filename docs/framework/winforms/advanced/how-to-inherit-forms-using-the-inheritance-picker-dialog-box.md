---
title: 'Porady: dziedziczenie formularzy korzystających z okna dialogowego selektora dziedziczenia'
ms.date: 03/30/2017
helpviewer_keywords:
- inheritance [Windows Forms], forms
- Inheritance Picker dialog box
- inherited forms [Windows Forms], creating
ms.assetid: 969b4c04-12aa-4297-93a2-0ae747447823
ms.openlocfilehash: 49c24b12616834ecc532a5568c0971e3dd75cfd8
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="how-to-inherit-forms-using-the-inheritance-picker-dialog-box"></a>Porady: dziedziczenie formularzy korzystających z okna dialogowego selektora dziedziczenia
Najprostszym sposobem dziedziczą formularza lub innego obiektu jest użycie **selektora dziedziczenia** okno dialogowe. Dzięki temu można korzystać z interfejsów kodu lub użytkownika (UI), zostały już utworzone w innych rozwiązań.  
  
> [!NOTE]
>  Aby dziedziczyć z formularza z **selektora dziedziczenia** okno dialogowe projekt zawierający formularz musi są wbudowane w pliku wykonywalnego lub DLL. Aby utworzyć projekt, wybierz **Kompiluj rozwiązanie** z **kompilacji** menu.  
>   
>  Okna dialogowe i polecenia menu mogą się różnić od tych opisanych w Pomocy, w zależności od ustawień aktywnych lub wydania. Aby zmienić ustawienia, wybierz **Import i eksport ustawień** na **narzędzia** menu. Aby uzyskać więcej informacji, zobacz [Dostosowywanie ustawień środowiska w programie Visual Studio](http://msdn.microsoft.com/library/22c4debb-4e31-47a8-8f19-16f328d7dcd3).  
  
### <a name="to-create-a-windows-form-inherited-from-an-existing-form-by-using-the-inheritance-picker"></a>Do tworzenia formularzy systemu Windows dziedziczone z istniejącego formularza za pomocą selektora dziedziczenia  
  
1.  Z **projektu** menu, wybierz **dodać formularza systemu Windows**.  
  
     **Dodaj nowy element** zostanie otwarte okno dialogowe.  
  
2.  Wybierz **dziedziczone formularza** szablonu i nazywa je w **nazwa** pole. Kliknij przycisk **Dodaj** przycisk, aby kontynuować.  
  
     **Selektora dziedziczenia** zostanie otwarte okno dialogowe. Jeśli bieżący projekt zawiera formularze, zostaną one wyświetlone w **selektora dziedziczenia** okno dialogowe.  
  
3.  Dziedziczenie z formularza w innym zestawie, kliknij przycisk **Przeglądaj** przycisku.  
  
4.  W ramach **wybierz plik, który zawiera składnik do dziedziczenia** okno dialogowe pola, przejdź do projektu zawierającego formularza lub chcesz modułu.  
  
5.  Kliknij nazwę pliku .exe lub dll, aby go zaznaczyć, a następnie kliknij przycisk **Otwórz** przycisku.  
  
     Nastąpi powrót do **selektora dziedziczenia** okno dialogowe, gdy składnik zostanie wyświetlony, wraz z projektu, w którym znajduje się.  
  
6.  Wybierz składnik.  
  
     W **Eksploratora rozwiązań**, składnik zostanie dodany do projektu. Jeśli ma ona interfejsu użytkownika, kontrolek, które są częścią dziedziczone formularza będą oznaczone znakiem symbolu (![VisualBasicInheritanceSymbol — zrzut ekranu](../../../../docs/framework/winforms/advanced/media/vbinheritanceglyph.gif "vbInheritanceGlyph")), i po wybraniu ma obramowanie wskazujący poziom zabezpieczeń, między formantem w formularzu podklasy. W poniższej tabeli wymieniono zachowania, które odpowiadają różnych poziomów ochrony.  
  
    |Poziom kontroli zabezpieczeń|Interakcja dostępne za pośrednictwem projektanta i edytora kodu z formularzem dziedziczone|  
    |-------------------------------|--------------------------------------------------------------------------------|  
    |Public|Standardowa obramowanie z uchwytów: formant może o rozmiarze i przenieść. Kontrolka jest możliwy wewnętrznie przez klasę, która deklaruje on i zewnętrznie innych klas.|  
    |Protected|Standardowa obramowanie z uchwytów: formant może o rozmiarze i przenieść. Możliwy jest wewnętrznie przez klasę, która deklaruje on i każdej klasy, która dziedziczy z klasy nadrzędnej, ale nie są dostępne dla klasy zewnętrznych.|  
    |Chronionych wewnętrznych (chronionych Friend w języku Visual Basic)|Standardowa obramowanie z uchwytów: formant może o rozmiarze i przenieść. Możliwy jest wewnętrznie przez klasę, która deklaruje on, każda klasa, która dziedziczy z klasy nadrzędnej oraz o innych elementach członkowskich zestawu, który go zawiera.|  
    |Wewnętrzny (Friend w języku Visual Basic)|Standardowa obramowanie z dojść zmiany rozmiaru, pokazywane w formularzu właściwości widoczne w **właściwości** okna. Jednak wszystkie aspekty formantu zostanie uwzględniony tylko do odczytu. Nie można przenieść lub rozmiar formantu ani zmienić jego właściwości. Jeśli formant jest kontenerem dla innych formantów, takich jak pole grupy, nie można dodać nowe formanty i nie można usunąć istniejących formantów, nawet jeśli te rozwiązania, zostały publicznego. Formant jest dostępny tylko w innych elementach członkowskich zestawu, który go zawiera.|  
    |Private|Standardowa obramowanie z dojść zmiany rozmiaru, pokazywane w formularzu właściwości widoczne w **właściwości** okna. Jednak wszystkie aspekty formantu zostanie uwzględniony tylko do odczytu. Nie można przenieść lub rozmiar formantu ani zmienić jego właściwości. Jeśli formant jest kontenerem dla innych formantów, takich jak pole grupy, nie można dodać nowe formanty i nie można usunąć istniejących formantów, nawet jeśli te rozwiązania, zostały publicznego. Kontrolka jest dostępny tylko przez klasę, która deklaruje go.|  
  
     Aby uzyskać informacje o tym, jak zmienić wygląd formularza podstawowego, zobacz [efekty modyfikowania wyglądu formularza podstawowego](../../../../docs/framework/winforms/advanced/effects-of-modifying-base-form-appearance.md).  
  
    > [!NOTE]
    >  Połączenie dziedziczone formanty i składniki ze standardowych kontrolek i składników w formularzach systemu Windows, mogą wystąpić powoduje konflikt z kolejność z. Problem można rozwiązać, zmieniając kolejność, które jest realizowane przez kliknięcie w **Format** menu i wskazujący **kolejności**, a następnie klikając pozycję **Przesuń na wierzch** lub  **Wyślij do tyłu**. Aby uzyskać więcej informacji o porządek formantów, zobacz [porady: warstwa obiektów na formularzach systemu Windows](../../../../docs/framework/winforms/controls/how-to-layer-objects-on-windows-forms.md).  
  
## <a name="see-also"></a>Zobacz też  
 [Inherits, instrukcja](~/docs/visual-basic/language-reference/statements/inherits-statement.md)  
 [using](~/docs/csharp/language-reference/keywords/using.md)  
 [Efekty modyfikowania wyglądu formularza podstawowego](../../../../docs/framework/winforms/advanced/effects-of-modifying-base-form-appearance.md)  
 [Formularze Windows Forms — dziedziczenie wizualizacji](../../../../docs/framework/winforms/advanced/windows-forms-visual-inheritance.md)

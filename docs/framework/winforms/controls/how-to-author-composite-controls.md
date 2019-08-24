---
title: 'Instrukcje: autoryzowanie kontrolek złożonych'
ms.date: 03/30/2017
helpviewer_keywords:
- UserControl class [Windows Forms], creating composite controls
- user controls [Windows Forms], creating
- user controls [Windows Forms], inheriting from
- composite controls [Windows Forms], creating
ms.assetid: 79c9cf05-5ab6-4a18-886d-88a64748b098
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: 08cb07ceebf08b3096415f9b7370e2d955152cb6
ms.sourcegitcommit: 121ab70c1ebedba41d276e436dd2b1502748a49f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/24/2019
ms.locfileid: "70015935"
---
# <a name="how-to-author-composite-controls"></a>Instrukcje: Tworzenie złożonych kontrolek

Kontrolki złożone mogą być stosowane na wiele sposobów. Można je tworzyć w ramach projektu aplikacji klasycznych systemu Windows i używać ich tylko na formularzach w projekcie. Można też tworzyć je w projekcie biblioteki formantów systemu Windows, kompilować projekt do zestawu i używać kontrolek w innych projektach. Można nawet dziedziczyć z nich i użyć dziedziczenia wizualnego, aby szybko dostosować je do specjalnych celów.

## <a name="to-author-a-composite-control"></a>Aby utworzyć formant złożony

1. W programie Visual Studio Utwórz nowy projekt **aplikacji systemu Windows** , a następnie nadaj mu nazwę **DemoControlHost**.

2. W menu **projekt** kliknij polecenie **Dodaj kontrolkę użytkownika**.

3. W oknie dialogowym **Dodaj nowy element** Nadaj plikowi klasy (plik VB lub CS) nazwę, która ma mieć formant złożony.

4. Wybierz przycisk **Dodaj** , aby utworzyć plik klasy dla formantu złożonego.

5. Dodaj kontrolki z **przybornika** do powierzchni formantu złożonego.

6. Umieść kod w procedurach zdarzeń, aby obsłużyć zdarzenia wywoływane przez formant złożony lub jego elementy sterujące.

7. Zamknij projektanta dla kontrolki złożonej i Zapisz plik po wyświetleniu monitu.

8. Na **kompilacji** menu, kliknij przycisk **Kompiluj rozwiązanie**.

     Projekt musi być skompilowany, aby formanty niestandardowe były wyświetlane w przyborniku.

9. Użyj karty **DemoControlHost** przybornika, aby dodać wystąpienia formantu do `Form1`programu.

## <a name="to-author-a-control-class-library"></a>Aby utworzyć bibliotekę klas formantów

1. Otwórz nowy projekt **biblioteki formantów systemu Windows** .

     Domyślnie projekt zawiera formant złożony.

2. Dodaj kontrolki i kod zgodnie z opisem w powyższej procedurze.

3. Wybierz kontrolkę, której klasy nie chcesz zmienić, i ustaw właściwość Modyfikatory tej kontrolki na **prywatną**.

4. Skompiluj bibliotekę DLL.

## <a name="to-inherit-from-a-composite-control-in-a-control-class-library"></a>Aby dziedziczyć z formantu złożonego w bibliotece klas formantów

1. W menu **plik** wskaż polecenie **Dodaj** i wybierz pozycję **Nowy projekt** , aby dodać nowy projekt **aplikacji systemu Windows** do rozwiązania.

2. W **Eksplorator rozwiązań**kliknij prawym przyciskiem myszy folder **odwołania** dla nowego projektu i wybierz polecenie **Dodaj odwołanie** , aby otworzyć okno dialogowe **Dodawanie odwołania** .

3. Wybierz kartę **projekty** i kliknij dwukrotnie projekt Biblioteka kontrolek.

4. Na **kompilacji** menu, kliknij przycisk **Kompiluj rozwiązanie**.

5. W **Eksplorator rozwiązań**kliknij prawym przyciskiem myszy projekt Biblioteka formantów i wybierz polecenie **Dodaj nowy element** z menu skrótów.

6. Wybierz **Dziedziczony szablon kontrolki użytkownika** w oknie dialogowym **Dodaj nowy element** .

7. W oknie dialogowym **Selektor dziedziczenia** kliknij dwukrotnie formant, z którego chcesz dziedziczyć.

     Do projektu zostanie dodany nowy formant.

8. Otwórz projektanta wizualnego dla nowej kontrolki i Dodaj dodatkowe kontrolki elementów.

     Można zobaczyć kontrolki elementów, które zostały odziedziczone z formantu złożonego w bibliotece DLL, i można zmienić właściwości formantów, których właściwość **modyfikatorów** jest publiczna. Nie można zmienić właściwości kontrolki, której właściwość **modyfikatorów** jest **prywatna**.

## <a name="see-also"></a>Zobacz także

- [Przewodnik: Tworzenie kontrolki złożonej](walkthrough-authoring-a-composite-control-with-visual-csharp.md)
- [Przewodnik: Dziedziczenie z kontrolki Windows Forms](walkthrough-inheriting-from-a-windows-forms-control-with-visual-csharp.md)
- [Zalecenia dotyczące typu kontrolki](control-type-recommendations.md)
- [Instrukcje: Kontrolki autora dla Windows Forms](how-to-author-controls-for-windows-forms.md)
- [Różne typy kontrolek niestandardowych](varieties-of-custom-controls.md)

---
title: 'Porady: dziedziczenie z klasy formantów'
ms.date: 03/30/2017
helpviewer_keywords:
- inheritance [Windows Forms], Windows Forms custom controls
- Control class [Windows Forms], inheriting from
- custom controls [Windows Forms], inheritance
- OnPaint method [Windows Forms]
- custom controls [Windows Forms], creating
ms.assetid: 46ba0df3-5cf7-443c-a3b4-a72660172476
ms.openlocfilehash: da80d46f27d7cd721af7a9600d2b0cde84876d23
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33534586"
---
# <a name="how-to-inherit-from-the-control-class"></a>Porady: dziedziczenie z klasy formantów
Jeśli chcesz utworzyć całkowicie niestandardowego formantu do użycia na formularzu systemu Windows, należy dziedziczyć z <xref:System.Windows.Forms.Control> klasy. Podczas dziedziczenia z <xref:System.Windows.Forms.Control> klasy wymaga wykonania więcej planowania i wdrażania, również zapewnia ona największą gamę opcji. Podczas dziedziczenia z <xref:System.Windows.Forms.Control>, dziedziczą bardzo podstawowe funkcje, dzięki formanty pracy. Funkcje związane z <xref:System.Windows.Forms.Control> klasy obsługi danych wejściowych użytkownika za pomocą klawiatury i myszy, definiuje granice i rozmiar formantu zapewnia obsługi systemu windows i zapewnia obsługi wiadomości i zabezpieczeń. Nie obejmuje żadnych rysowania, czyli w tym przypadku rzeczywistych renderowania formantu interfejsu graficznego, nie jest ona zawierać żadnych funkcji interakcji użytkownika. Należy podać wszystkie te aspekty za pomocą kodu niestandardowego.  
  
> [!NOTE]
>  Okna dialogowe i polecenia menu mogą się różnić od tych opisanych w Pomocy, w zależności od ustawień aktywnych lub wydania. Aby zmienić ustawienia, wybierz **Import i eksport ustawień** na **narzędzia** menu. Aby uzyskać więcej informacji, zobacz [Dostosowywanie ustawień środowiska w programie Visual Studio](http://msdn.microsoft.com/library/22c4debb-4e31-47a8-8f19-16f328d7dcd3).  
  
### <a name="to-create-a-custom-control"></a>Można utworzyć niestandardowego formantu  
  
1.  Utwórz nową **aplikacji systemu Windows** lub **Biblioteka formantów systemu Windows** projektu.  
  
2.  Z **projektu** menu, wybierz **Dodaj klasę**.  
  
3.  W **Dodaj nowy element** okno dialogowe, kliknij przycisk **formant niestandardowy**.  
  
     Formant niestandardowy jest dodawany do projektu.  
  
4.  Naciśnij klawisz F7, aby otworzyć **edytora kodu** dla formantu niestandardowego.  
  
5.  Zlokalizuj <xref:System.Windows.Forms.Control.OnPaint%2A> metodę, która będzie pusty, z wyjątkiem wywołanie <xref:System.Windows.Forms.Control.OnPaint%2A> metody klasy podstawowej.  
  
6.  Zmodyfikuj kod, aby uwzględnić wszystkie niestandardowe rysowania dla formantu.  
  
     Aby uzyskać informacje dotyczące pisania kodu do renderowania grafiki dla formantów, zobacz [niestandardowe malowanie i renderowanie formantu](../../../../docs/framework/winforms/controls/custom-control-painting-and-rendering.md).  
  
7.  Implementuje żadnych niestandardowych metod, właściwości lub zdarzeń, zawierające formantu.  
  
8.  Zapisz i przetestować formantu.  
  
## <a name="see-also"></a>Zobacz też  
 [Różne typy kontrolek niestandardowych](../../../../docs/framework/winforms/controls/varieties-of-custom-controls.md)  
 [Instrukcje: dziedziczenie z klasy UserControl](../../../../docs/framework/winforms/controls/how-to-inherit-from-the-usercontrol-class.md)  
 [Instrukcje: dziedziczenie z istniejących kontrolek formularzy Windows Forms](../../../../docs/framework/winforms/controls/how-to-inherit-from-existing-windows-forms-controls.md)  
 [Instrukcje: tworzenie kontrolek dla formularzy Windows Forms](../../../../docs/framework/winforms/controls/how-to-author-controls-for-windows-forms.md)  
 [Rozwiązywanie problemów z odziedziczonymi programami obsługi zdarzeń w języku Visual Basic](~/docs/visual-basic/programming-guide/language-features/events/troubleshooting-inherited-event-handlers.md)  
 [Opracowywanie kontrolek formularzy Windows Forms w czasie projektowania](../../../../docs/framework/winforms/controls/developing-windows-forms-controls-at-design-time.md)

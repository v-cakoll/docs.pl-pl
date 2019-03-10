---
title: Malowanie i renderowanie formantu niestandardowego
ms.date: 03/30/2017
helpviewer_keywords:
- custom controls [Windows Forms], rendering
- custom controls [Windows Forms], painting
- user controls [Windows Forms], painting
ms.assetid: a09dbf76-0966-4cbf-a66a-2083ba98e068
ms.openlocfilehash: ec9002ffa4a7e2c82f59d52344764a01afe4c568
ms.sourcegitcommit: 160a88c8087b0e63606e6e35f9bd57fa5f69c168
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/09/2019
ms.locfileid: "57722142"
---
# <a name="custom-control-painting-and-rendering"></a>Malowanie i renderowanie formantu niestandardowego
Malowanie niestandardowych formantów jest jednym z wielu zadań skomplikowane, łatwe w programie .NET Framework. Podczas tworzenia niestandardowego formantu, masz wiele opcji dotyczących kontroli nad wyglądem graficznego. Jeśli tworzony formant, który dziedziczy z `Control`, należy podać kod, który umożliwia formantu do renderowania jej graficzną reprezentację. Jeśli utworzysz formant użytkownika przez dziedziczenie z `UserControl`, lub są dziedziczone z jednej z kontrolek Windows Forms, może zastąpić standardowa graficzną reprezentację i podanie kodu grafiki. Jeśli chcesz udostępnić niestandardowe renderowanie kontrolek składowych `UserControl` tworzenia, opcje stają się bardziej ograniczone, ale nadal zezwalają na szeroką gamę możliwości graficznego dla aplikacji i formantów.  
  
## <a name="in-this-section"></a>W tej sekcji  
 [Renderowanie kontrolki formularzy Windows Forms](rendering-a-windows-forms-control.md)  
 Pokazuje, jak program logikę, która wyświetla kontrolkę.  
  
 [Kontrolki rysowane przez użytkownika](user-drawn-controls.md)  
 Zestawienie etapy pisania i zastępowanie kod renderowania dla formantu.  
  
 [Kontrolki składników](constituent-controls.md)  
 W tym artykule opisano, jak implementować niestandardowe renderowanie kodu dla składowych kontrolek formularzy i kontrolek użytkownika.  
  
 [Instrukcje: Ukrywanie formantu w czasie wykonywania](how-to-make-your-control-invisible-at-run-time.md)  
 Ilustruje sposób używania <xref:System.Windows.Forms.Control.Visible%2A> właściwości, aby ukryć i pokazać kontrolki.  
  
 [Instrukcje: Zachować kontrolę z przezroczystym tłem](how-to-give-your-control-a-transparent-background.md)  
 Ilustruje sposób używania <xref:System.Windows.Forms.Control.SetStyle%2A> metodę w celu utworzenia kolor tła nieprzezroczyste, przezroczysta lub częściowo przezroczyste.  
  
 [Renderowanie kontrolek przy użyciu stylów wizualnych](rendering-controls-with-visual-styles.md)  
 Przedstawia sposób renderowania kontrolek przy użyciu stylów wizualnych w systemach operacyjnych, które je obsługują.  
  
## <a name="reference"></a>Tematy pomocy  
 <xref:System.Windows.Forms.Control>  
 Zawiera opis tej klasy i zawiera linki do wszystkich jej członków.  
  
 <xref:System.Windows.Forms.UserControl>  
 Zawiera opis tej klasy i zawiera linki do wszystkich jej członków.  
  
 <xref:System.Windows.Forms.Control.OnPaint%2A>  
 W tym artykule opisano tę metodę.  
  
## <a name="related-sections"></a>Sekcje pokrewne  
 [Instrukcje: Tworzenie obiektów graficznych do rysowania](../advanced/how-to-create-graphics-objects-for-drawing.md)  
 Wprowadza [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)] funkcje grafiki z programu Visual Studio perspektywy i udostępnia łącza do dodatkowych informacji.  
  
 [Różne typy kontrolek niestandardowych](varieties-of-custom-controls.md)  
 W tym artykule opisano rodzaje niestandardowe formanty, które można tworzyć.

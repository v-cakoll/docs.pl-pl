---
title: Najlepsze praktyki dotyczące formantu TableLayoutPanel
ms.date: 03/30/2017
helpviewer_keywords:
- layout [Windows Forms]
- TableLayoutPanel control [Windows Forms], best practices
- forms [Windows Forms], best practices
- AutoSize property [Windows Forms], tableLayoutPanel control
- controls [Windows Forms], sizing
- TableLayoutPanel control [Windows Forms], AutoSize behavior
- layout [Windows Forms], AutoSize
- layout [Windows Forms], best practices
- best practices [Windows Forms], tableLayoutPanel control
- sizing [Windows Forms], automatic
- automatic sizing
ms.assetid: b6706efb-d7a4-45ec-8cf4-08fa993e3afb
ms.openlocfilehash: 57abf3527af146f1ce918bcabbc6a5a34bfb9b34
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/08/2019
ms.locfileid: "59222331"
---
# <a name="best-practices-for-the-tablelayoutpanel-control"></a>Najlepsze praktyki dotyczące formantu TableLayoutPanel
<xref:System.Windows.Forms.TableLayoutPanel> Kontroli udostępnia funkcje zaawansowane układu, które należy rozważyć przed użyciem na formularzach Windows.  
  
## <a name="recommendations"></a>Zalecenia  
 Poniższe zalecenia ułatwi użycie <xref:System.Windows.Forms.TableLayoutPanel> kontrolki do jej zaletą najlepsze.  
  
### <a name="targeted-use"></a>Użyj docelowego  
 Użyj <xref:System.Windows.Forms.TableLayoutPanel> kontrolować rzadko. We wszystkich sytuacjach wymagających o zmiennym rozmiarze układu nie należy używać go. Na poniższej liście opisano układy, korzystają najbardziej z użycia zestawów <xref:System.Windows.Forms.TableLayoutPanel> sterowania:  
  
-   Układy, w których istnieje wiele części formularza, które proporcjonalnie do siebie nawzajem.  
  
-   Układy zostanie zmodyfikowany lub generowany dynamicznie w czasie wykonywania, takich jak formularze wprowadzania danych, które mają pól możliwych do dostosowania użytkownika dodawane lub odejmowane na podstawie preferencji.  
  
-   Układy, które powinny pozostać w ogólnej o stałym rozmiarze. Na przykład masz okno dialogowe, które powinny pozostać mniejsza niż 800 x 600, ale trzeba obsługiwać zlokalizowane ciągi.  
  
 Na poniższej liście opisano układy nie osiągają znaczne korzyści z używania <xref:System.Windows.Forms.TableLayoutPanel> sterowania:  
  
-   Proste formularze wprowadzania danych z jedną kolumną etykiet i jedną kolumnę obszarów wprowadzania tekstu.  
  
-   Formularze za pomocą pojedynczego dużych wyświetlać obszar, który należy wypełnić całe dostępne miejsce po wystąpieniu zmiany rozmiaru. Na przykład jest formularz, który wyświetla jedną <xref:System.Windows.Forms.PropertyGrid> kontroli. Zakotwiczanie, użyj w tym przypadku ponieważ nic powinni rozwinąć pozycję gdy zmieniany jest rozmiar formularza.  
  
 Wybierz uważnie, które kontrolki, które muszą być w <xref:System.Windows.Forms.TableLayoutPanel> kontroli. Jeśli dysponujesz miejscem na tekście rośnie o 30%, za pomocą Zakotwiczanie, rozważ użycie <xref:System.Windows.Forms.Control.Anchor%2A> tylko właściwości. Jeśli miejsce wymagane przez układ można oszacować, użyj <xref:System.Windows.Forms.Control.Dock%2A> i <xref:System.Windows.Forms.Control.Anchor%2A> jest łatwiejsze niż szacowania szczegóły ilość wolnego miejsca i <xref:System.Windows.Forms.Control.AutoSize%2A> zachowanie.  
  
 Ogólnie rzecz biorąc, podczas projektowania układu z <xref:System.Windows.Forms.TableLayoutPanel> sterowania, projekt powinien być tak proste, jak to możliwe.  
  
### <a name="use-the-document-outline-window"></a>Okno konspektu dokumentu  
 Okno konspektu dokumentu zapewnia układu można używać do manipulowania relacji porządek i nadrzędny podrzędny, dla Twoich kontrolek w widoku drzewa. Z **menu Widok**, wybierz opcję **Windows inne**, a następnie wybierz **konspekt dokumentu**.  
  
### <a name="avoid-nesting"></a>Uniknąć zagnieżdżania  
 Należy unikać zagnieżdżanie innych <xref:System.Windows.Forms.TableLayoutPanel> kontrolki w ramach <xref:System.Windows.Forms.TableLayoutPanel> kontroli. Debugowanie układy zagnieżdżonych może być trudne.  
  
### <a name="avoid-visual-inheritance"></a>Należy unikać dziedziczenie Visual  
 <xref:System.Windows.Forms.TableLayoutPanel> Formant nie obsługuje dziedziczenie visual w programie Windows Forms Designer. A <xref:System.Windows.Forms.TableLayoutPanel> formantu w klasie pochodnej pojawia się jako "zablokowany" w czasie projektowania.  
  
## <a name="see-also"></a>Zobacz także

- <xref:System.Windows.Forms.TableLayoutPanel>
- <xref:System.Windows.Forms.FlowLayoutPanel>

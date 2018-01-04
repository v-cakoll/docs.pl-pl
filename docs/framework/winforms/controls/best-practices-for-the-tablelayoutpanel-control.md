---
title: "Najlepsze praktyki dotyczące formantu TableLayoutPanel"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
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
caps.latest.revision: "11"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 8f2c5a16ea1f07f7688c9df14bdb6b29350f3acf
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="best-practices-for-the-tablelayoutpanel-control"></a>Najlepsze praktyki dotyczące formantu TableLayoutPanel
<xref:System.Windows.Forms.TableLayoutPanel> Kontrola zapewnia układu zaawansowane funkcje, które należy rozważyć przed użyciem na formularzach systemu Windows.  
  
## <a name="recommendations"></a>Zalecenia  
 Poniższe zalecenia pomogą użyj <xref:System.Windows.Forms.TableLayoutPanel> formantu, aby jego najważniejsze korzyści.  
  
### <a name="targeted-use"></a>Użyj docelowych  
 Użyj <xref:System.Windows.Forms.TableLayoutPanel> kontrolować oszczędnie. W sytuacjach wszystkie, które wymagają układu o zmiennym rozmiarze nie należy używać go. Poniższa lista zawiera opis układy, korzystają najbardziej z użycia <xref:System.Windows.Forms.TableLayoutPanel> sterowania:  
  
-   Układy, w których istnieje wiele części formularza, które proporcjonalnie do siebie.  
  
-   Układy, które zostaną zmodyfikowane lub generowane dynamicznie w czasie wykonywania, takie jak formularze wprowadzania danych, których można dostosowywać użytkownika pola dodane lub usunięte zgodnie z preferencjami.  
  
-   Układy, które powinny pozostać w ogólnej stałym rozmiarze. Na przykład może być okno dialogowe, które powinny pozostać mniejsza niż 800 x 600, ale należy do obsługi zlokalizowanych ciągów.  
  
 Poniższa lista zawiera opis układy nie znacznie korzyści ze stosowania <xref:System.Windows.Forms.TableLayoutPanel> sterowania:  
  
-   Proste formularze wprowadzania danych z jedną kolumną etykiety i pojedynczej kolumny obszarów wprowadzania tekstu.  
  
-   Formularze za pomocą jednej dużych wyświetlić obszar, który powinien wypełnił dostępne miejsce podczas zmiany rozmiaru. Na przykład jest formularz, który wyświetla pojedynczy <xref:System.Windows.Forms.PropertyGrid> formantu. Zakotwiczanie, użyj w tym przypadku, ponieważ nic rozszerzyć gdy zmieniany jest rozmiar formularza.  
  
 Wybierz uważnie, które kontrolki musi być <xref:System.Windows.Forms.TableLayoutPanel> formantu. Jeśli dysponujesz miejscem na tekst zwiększa się o 30% przy użyciu Zakotwiczanie, rozważ użycie <xref:System.Windows.Forms.Control.Anchor%2A> tylko właściwości. Jeśli można oszacować miejsca wymaganego przez układ, użycie <xref:System.Windows.Forms.Control.Dock%2A> i <xref:System.Windows.Forms.Control.Anchor%2A> jest łatwiejsze niż Szacowanie szczegóły pozostałego miejsca i <xref:System.Windows.Forms.Control.AutoSize%2A> zachowanie.  
  
 Na ogół podczas projektowania układu z <xref:System.Windows.Forms.TableLayoutPanel> kontrolować, projekt powinien być tak proste, jak to możliwe.  
  
### <a name="use-the-document-outline-window"></a>Okno konspektu dokumentu  
 Okno konspektu dokumentu umożliwia układu, która służy do manipulowania relacje porządek i nadrzędny podrzędny dla Twoich formantów w widoku drzewa. Z **menu Widok**, wybierz pozycję **inne okna**, a następnie wybierz pozycję **konspekt dokumentu**.  
  
### <a name="avoid-nesting"></a>Unikaj zagnieżdżania  
 Unikaj zagnieżdżanie innych <xref:System.Windows.Forms.TableLayoutPanel> steruje w obrębie <xref:System.Windows.Forms.TableLayoutPanel> formantu. Debugowanie zagnieżdżonych układów może być trudne.  
  
### <a name="avoid-visual-inheritance"></a>Unikaj dziedziczenie Visual  
 <xref:System.Windows.Forms.TableLayoutPanel> Formant nie obsługuje dziedziczenia visual w narzędziu Projektant dla formularzy systemu Windows. A <xref:System.Windows.Forms.TableLayoutPanel> kontroli w klasie pochodnej pojawia się jako "zablokowana" w czasie projektowania.  
  
## <a name="see-also"></a>Zobacz też  
 <xref:System.Windows.Forms.TableLayoutPanel>  
 <xref:System.Windows.Forms.FlowLayoutPanel>

---
title: 'Wskazówki: przeprowadzanie typowych zadań z tagami inteligentnymi na kontrolkach formularzy systemu Windows'
ms.date: 03/30/2017
helpviewer_keywords:
- DesignerAction object model
- smart tags
- designer actions
ms.assetid: cac337e6-00f6-4584-80f4-75728f5ea113
ms.openlocfilehash: a558f6d274f260fc91fd140e9dae2c740b1ae00d
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="walkthrough-performing-common-tasks-using-smart-tags-on-windows-forms-controls"></a>Wskazówki: przeprowadzanie typowych zadań z tagami inteligentnymi na kontrolkach formularzy systemu Windows
Podczas przygotowywania formularzy i formantów w aplikacji formularzy systemu Windows, istnieje wiele zadań, które będą wykonywane wielokrotnie. Oto niektóre z najczęściej wykonywanych zadań, które wystąpią:  
  
-   Dodawanie lub usuwanie karty na <xref:System.Windows.Forms.TabControl>.  
  
-   Dokowanie formantu do elementu nadrzędnego.  
  
-   Zmiana orientacji <xref:System.Windows.Forms.SplitContainer> formantu.  
  
 Aby przyspieszyć programowanie, wielu formantów oferują tagi inteligentne, które są menu kontekstowe, które umożliwiają wykonywanie typowych zadań, takich jak te w jednym gestu w czasie projektowania. Zadania te są nazywane *zleceń tagów inteligentnych*.  
  
 Tagi inteligentne być dołączony do wystąpienia formantu przez jego okres istnienia w Projektancie i są zawsze dostępne.  
  
 Zadania przedstawione w tym przewodniku obejmują:  
  
-   Tworzenie projektu formularzy systemu Windows  
  
-   Z tagami inteligentnymi  
  
-   Włączanie i wyłączanie tagi inteligentne  
  
 Gdy skończysz, konieczne będzie zrozumienia rolę odgrywaną przez te funkcje ważne układu.  
  
> [!NOTE]
>  Okna dialogowe i polecenia menu mogą się różnić od tych opisanych w Pomocy, w zależności od ustawień aktywnych lub wydania. Aby zmienić ustawienia, wybierz **Import i eksport ustawień** na **narzędzia** menu. Aby uzyskać więcej informacji, zobacz [Dostosowywanie ustawień środowiska w programie Visual Studio](http://msdn.microsoft.com/library/22c4debb-4e31-47a8-8f19-16f328d7dcd3).  
  
## <a name="creating-the-project"></a>Tworzenie projektu  
 Pierwszym krokiem jest utworzenie projektu i konfigurowanie formularza.  
  
#### <a name="to-create-the-project"></a>Aby utworzyć projekt  
  
1.  Utwórz projekt aplikacji systemu Windows o nazwie "SmartTagsExample". Aby uzyskać więcej informacji, zobacz [porady: Tworzenie projektu aplikacji Windows](http://msdn.microsoft.com/library/b2f93fed-c635-4705-8d0e-cf079a264efa).  
  
2.  Wybierz formularza w **Projektant formularzy systemu Windows**.  
  
## <a name="using-smart-tags"></a>Z tagami inteligentnymi  
 Tagi inteligentne są zawsze dostępne w czasie projektowania w formantach, które oferują je.  
  
#### <a name="to-use-smart-tags"></a>Aby użyć tagi inteligentne  
  
1.  Przeciągnij <xref:System.Windows.Forms.TabControl> z **przybornika** na formularzu. Należy zwrócić uwagę symbolu tagów inteligentnych (![symbol tagu inteligentnego](../../../../docs/framework/winforms/controls/media/vs-winformsmttagglyph.gif "VS_WinFormSmtTagGlyph")) wyświetlany na stronie z <xref:System.Windows.Forms.TabControl>.  
  
2.  Kliknij symbol tagów inteligentnych. Wybierz z menu skrótów wyświetlane obok symbolu **Dodaj kartę** elementu. Sprawdź, czy nowa strona karty została dodana do <xref:System.Windows.Forms.TabControl>.  
  
3.  Przeciągnij <xref:System.Windows.Forms.TableLayoutPanel> kontrolować z **przybornika** na formularzu.  
  
4.  Kliknij symbol tagów inteligentnych. Wybierz z menu skrótów wyświetlane obok symbolu **Dodaj kolumnę** elementu. Sprawdź, czy nowa kolumna została dodana do <xref:System.Windows.Forms.TableLayoutPanel> formantu.  
  
5.  Przeciągnij <xref:System.Windows.Forms.SplitContainer> kontrolować z **przybornika** na formularzu.  
  
6.  Kliknij symbol tagów inteligentnych. Wybierz z menu skrótów wyświetlane obok symbolu **orientacji poziomej rozdzielacza** elementu. Że <xref:System.Windows.Forms.SplitContainer> pasek podziału formantu jest teraz orientacji poziomej.  
  
## <a name="see-also"></a>Zobacz też  
 <xref:System.Windows.Forms.TextBox>  
 <xref:System.Windows.Forms.TabControl>  
 <xref:System.Windows.Forms.SplitContainer>  
 <xref:System.ComponentModel.Design.DesignerActionList>  
 [Wskazówki: Dodawanie tagów inteligentnych do składnika formularzy systemu Windows](http://msdn.microsoft.com/library/a6814169-fa7d-4527-808c-637ca5c95f63)

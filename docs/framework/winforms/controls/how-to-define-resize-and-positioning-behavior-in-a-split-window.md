---
title: 'Porady: definiowanie zachowania dotyczącego zmieniania rozmiaru i pozycjonowania w podzielonym oknie'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- split windows [Windows Forms], resizing
- splitter windows [Windows Forms], resizing
- SplitContainer control [Windows Forms], resizing
ms.assetid: 9bf73f36-ed2d-4a02-b15a-0770eff4fdfa
ms.openlocfilehash: 015e93fb551b8d48b8a57662b8def61c3cb46c2a
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33531638"
---
# <a name="how-to-define-resize-and-positioning-behavior-in-a-split-window"></a>Porady: definiowanie zachowania dotyczącego zmieniania rozmiaru i pozycjonowania w podzielonym oknie
Panele <xref:System.Windows.Forms.SplitContainer> kontroli redagowanie również są zmiany rozmiaru i manipulowanie przez użytkowników. Jednak zostanie wystąpić sytuacje, kiedy można programowo zarządzać rozdzielacza, gdzie jest umieszczony i w jakim stopniu można go przenieść.  
  
 <xref:System.Windows.Forms.SplitContainer.SplitterIncrement%2A> Właściwości i innych właściwości w <xref:System.Windows.Forms.SplitContainer> kontroli zapewniają precyzyjną kontrolę zachowania interfejsu użytkownika w zależności od potrzeb. W poniższej tabeli przedstawiono te właściwości.  
  
|Nazwa|Opis|  
|----------|-----------------|  
|<xref:System.Windows.Forms.SplitContainer.IsSplitterFixed%2A> Właściwość|Określa, czy rozdzielacz jest ruchomy za pomocą klawiatury lub myszy.|  
|<xref:System.Windows.Forms.SplitContainer.SplitterDistance%2A> Właściwość|Określa odległość w pikselach pasek podziału ruchomy od lewej lub górnej krawędzi.|  
|<xref:System.Windows.Forms.SplitContainer.SplitterIncrement%2A> Właściwość|Określa minimalny odstęp w pikselach, że rozdzielacza mogą być przenoszone przez użytkownika.|  
  
 W poniższym przykładzie modyfikuje <xref:System.Windows.Forms.SplitContainer.SplitterIncrement%2A> właściwości do utworzenia efektu "przyciąganie podziału"; gdy użytkownik przeciąga rozdzielacza, zwiększa narastająco w jednostkach 10 pikseli zamiast domyślnego 1.  
  
### <a name="to-define-splitcontainer-resize-behavior"></a>Aby określić zachowanie podczas zmiany rozmiaru SplitContainer  
  
1.  W procedurze, ustaw <xref:System.Windows.Forms.SplitContainer.SplitterIncrement%2A> właściwości do żądanego rozmiaru, dzięki czemu zostaje przywrócony zachowanie "przyciąganie" rozdzielacza.  
  
     W poniższym przykładzie kodu, w ramach formularza <xref:System.Windows.Forms.Form.Load> zdarzenie, podziału w <xref:System.Windows.Forms.SplitContainer> kontrola została ustawiona na przejście 10 pikseli podczas przeciągania.  
  
    ```vb  
    Private Sub Form1_Load(ByVal sender As System.Object, _  
        ByVal e As System.EventArgs) Handles MyBase.Load  
        Dim splitSnapper as new SplitContainer()  
        splitSnapper.SplitterIncrement = 10  
        splitSnapper.Dock = DockStyle.Fill  
        splitSnapper.Parent = me  
    End Sub  
    ```  
  
    ```csharp  
    private void Form1_Load(System.Object sender, System.EventArgs e)  
    {  
        SplitContainer splitSnapper = new SplitContainer();  
        splitSnapper.SplitterIncrement = 10;  
        splitSnapper.Dock = DockStyle.Fill;  
        splitSnapper.Parent = this;  
    }  
    ```  
  
     (Visual C#) Umieść następujący kod w Konstruktorze formularza, aby zarejestrować program obsługi zdarzeń.  
  
    ```csharp  
    this.Load += new System.EventHandler(this.Form1_Load);  
    ```  
  
     Przenoszenie rozdzielacza nieco do lewej lub prawej nie wpłyną zauważalny; Gdy wskaźnik myszy przechodzi 10 pikseli, rozdzielacza spowoduje przyciąganie do nowej pozycji.  
  
## <a name="see-also"></a>Zobacz też  
 <xref:System.Windows.Forms.SplitContainer>  
 <xref:System.Windows.Forms.SplitContainer.SplitterIncrement%2A>

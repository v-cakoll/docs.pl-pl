---
title: ImageList — Informacje o składniku
ms.date: 03/30/2017
f1_keywords:
- ImageList
helpviewer_keywords:
- collection controls [Windows Forms], images
- icon list control
- ImageList component [Windows Forms], about ImageList component
ms.assetid: 7e25d89b-5633-40c1-afc3-82e0e301ffa2
ms.openlocfilehash: b46204375cb046d637f4c9e1d888f37d10ea1f57
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/24/2020
ms.locfileid: "76728104"
---
# <a name="imagelist-component-overview-windows-forms"></a>ImageList — Informacje o składniku (Formularze systemu Windows)

Składnik <xref:System.Windows.Forms.ImageList> Windows Forms jest używany do przechowywania obrazów, które są następnie wyświetlane przez kontrolki. Lista obrazów umożliwia pisanie kodu dla jednego spójnego wykazu obrazów. Na przykład można obrócić obrazy wyświetlane przez formant <xref:System.Windows.Forms.Button> po prostu zmieniając właściwość <xref:System.Windows.Forms.ButtonBase.ImageIndex%2A> lub <xref:System.Windows.Forms.ButtonBase.ImageKey%2A> przycisku. Można także skojarzyć tę samą listę obrazów z wieloma kontrolkami. Na przykład jeśli używasz kontrolki <xref:System.Windows.Forms.ListView> i kontrolki <xref:System.Windows.Forms.TreeView> do wyświetlania tej samej listy plików, zmiana ikony pliku na liście obrazów spowoduje, że nowa ikona zostanie wyświetlona w obu widokach.

## <a name="using-imagelist-with-controls"></a>Używanie elementu ImageList z kontrolkami

Można użyć listy obrazów z dowolnym formantem, który ma właściwość `ImageList` — lub w przypadku kontrolki <xref:System.Windows.Forms.ListView>, <xref:System.Windows.Forms.ListView.SmallImageList%2A> i <xref:System.Windows.Forms.ListView.LargeImageList%2A> właściwości. Kontrolki, które mogą być skojarzone z listą obrazów, obejmują: <xref:System.Windows.Forms.ListView>, <xref:System.Windows.Forms.TreeView>, <xref:System.Windows.Forms.ToolBar>, <xref:System.Windows.Forms.TabControl>, <xref:System.Windows.Forms.Button>, <xref:System.Windows.Forms.CheckBox>, <xref:System.Windows.Forms.RadioButton>i <xref:System.Windows.Forms.Label> kontrolek. Aby skojarzyć listę obrazów z kontrolką, ustaw właściwość `ImageList` kontrolki na nazwę składnika <xref:System.Windows.Forms.ImageList>.

## <a name="key-properties"></a>Właściwości klucza

Właściwość Key składnika <xref:System.Windows.Forms.ImageList> jest <xref:System.Windows.Forms.ImageList.Images%2A>, która zawiera obrazy, które mają być używane przez skojarzoną kontrolkę. Do każdego pojedynczego obrazu można uzyskać dostęp za pomocą jego wartości indeksu lub klucza. Właściwość <xref:System.Windows.Forms.ImageList.ColorDepth%2A> określa liczbę kolorów, z którymi są renderowane obrazy. Wszystkie obrazy będą wyświetlane w tym samym rozmiarze, ustawiane przez właściwość <xref:System.Windows.Forms.ImageList.ImageSize%2A>. Obrazy, które są większe, są skalowane w celu dopasowania.

## <a name="see-also"></a>Zobacz także

- <xref:System.Windows.Forms.ImageList>
- [Instrukcje: dodawanie lub usuwanie obrazów za pomocą składnika ImageList formularzy Windows Forms](how-to-add-or-remove-images-with-the-windows-forms-imagelist-component.md)

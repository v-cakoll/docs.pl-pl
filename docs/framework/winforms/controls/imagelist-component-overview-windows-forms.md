---
title: ImageList — Informacje o składniku (Formularze systemu Windows)
ms.date: 03/30/2017
f1_keywords:
- ImageList
helpviewer_keywords:
- collection controls [Windows Forms], images
- icon list control
- ImageList component [Windows Forms], about ImageList component
ms.assetid: 7e25d89b-5633-40c1-afc3-82e0e301ffa2
ms.openlocfilehash: d4513439594c9bceac3463a5b878f9059a16046e
ms.sourcegitcommit: 8699383914c24a0df033393f55db3369db728a7b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/15/2019
ms.locfileid: "65645698"
---
# <a name="imagelist-component-overview-windows-forms"></a>ImageList — Informacje o składniku (Formularze systemu Windows)

Formularze Windows <xref:System.Windows.Forms.ImageList> składnik jest używany do przechowywania obrazów, które następnie mogą być wyświetlane przez formanty. Listy obrazów umożliwia pisanie kodu dla jednego, spójne katalog obrazów. Na przykład, można też obrócić obrazy wyświetlane przez <xref:System.Windows.Forms.Button> kontroli po prostu zmieniając przycisku <xref:System.Windows.Forms.ButtonBase.ImageIndex%2A> lub <xref:System.Windows.Forms.ButtonBase.ImageKey%2A> właściwości. Można również skojarzyć tę samą listę obrazów z wieloma formantami. Na przykład, jeśli używasz zarówno <xref:System.Windows.Forms.ListView> kontroli i <xref:System.Windows.Forms.TreeView> formantu, aby wyświetlić ta sama lista plików, zmieniając ikonę pliku z listy obrazów spowoduje, że nowa ikona pojawią się w obu widokach.

## <a name="using-imagelist-with-controls"></a>Używanie listy obrazów z kontrolkami

Za pomocą listy obrazów żadnego formantu, który ma `ImageList` właściwość — lub w przypadku właściwości <xref:System.Windows.Forms.ListView> kontroli <xref:System.Windows.Forms.ListView.SmallImageList%2A> i <xref:System.Windows.Forms.ListView.LargeImageList%2A> właściwości. Formanty, które mogą być skojarzone z listy obrazów obejmują: <xref:System.Windows.Forms.ListView>, <xref:System.Windows.Forms.TreeView>, <xref:System.Windows.Forms.ToolBar>, <xref:System.Windows.Forms.TabControl>, <xref:System.Windows.Forms.Button>, <xref:System.Windows.Forms.CheckBox>, <xref:System.Windows.Forms.RadioButton>, i <xref:System.Windows.Forms.Label> kontrolki. Aby skojarzyć listy obrazów z formantem, ustawić `ImageList` właściwość na nazwę <xref:System.Windows.Forms.ImageList> składnika.

## <a name="key-properties"></a>Właściwości klucza

Właściwość klucza <xref:System.Windows.Forms.ImageList> składnik to <xref:System.Windows.Forms.ImageList.Images%2A>, który zawiera obrazy, które ma być używany przez skojarzony formant. Każdy obraz poszczególnych może zostać oceniony przez jej wartość indeksu lub za pomocą klucza. <xref:System.Windows.Forms.ImageList.ColorDepth%2A> Właściwość określa liczbę kolorów, które obrazy są renderowane przy użyciu. Obrazy wszystkie wyświetlane są w taki sam rozmiar, ustawiane przez <xref:System.Windows.Forms.ImageList.ImageSize%2A> właściwości. Obrazy, które są większe zostaną odpowiednio dopasowane.

## <a name="see-also"></a>Zobacz także

- <xref:System.Windows.Forms.ImageList>
- [Instrukcje: Dodawanie lub usuwanie obrazów za pomocą składnika ImageList formularzy Windows](how-to-add-or-remove-images-with-the-windows-forms-imagelist-component.md)

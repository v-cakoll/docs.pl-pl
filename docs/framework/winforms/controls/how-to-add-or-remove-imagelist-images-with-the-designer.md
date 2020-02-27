---
title: 'Porady: dodawanie lub usuwanie obrazów ImageList przy użyciu narzędzia Projektant'
ms.date: 03/30/2017
helpviewer_keywords:
- ImageList component [Windows Forms], adding images
- ImageList component [Windows Forms], removing images
- images [Windows Forms], adding to ImageList component
ms.assetid: 5699b244-e37c-4d20-bc35-7441e55c1e3a
ms.openlocfilehash: cdc7b563a0ee4f8779b99b4e9a6786e78f8d500f
ms.sourcegitcommit: 44a7cd8687f227fc6db3211ccf4783dc20235e51
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/26/2020
ms.locfileid: "77628725"
---
# <a name="how-to-add-or-remove-imagelist-images-with-the-designer"></a>Porady: dodawanie lub usuwanie obrazów ImageList przy użyciu narzędzia Projektant

Do składnika <xref:System.Windows.Forms.ImageList> można dodawać obrazy na kilka różnych sposobów. Obrazy można dodawać bardzo szybko przy użyciu tagu inteligentnego skojarzonego z <xref:System.Windows.Forms.ImageList>lub jeśli ustawiasz kilka innych właściwości na <xref:System.Windows.Forms.ImageList>, może być wygodniejsze Dodawanie obrazów z okno Właściwości. Możesz również dodawać obrazy za pomocą kodu. Aby uzyskać więcej informacji na temat dodawania obrazów przy użyciu kodu, zobacz [How to: Dodawanie lub usuwanie obrazów za pomocą składnika Windows Forms ImageList](how-to-add-or-remove-images-with-the-windows-forms-imagelist-component.md). Zwykle wypełniany jest składnik <xref:System.Windows.Forms.ImageList> z obrazami, zanim zostanie on skojarzony z kontrolką, ale nie jest to wymagane.

### <a name="to-add-or-remove-images-by-using-the-properties-window"></a>Aby dodać lub usunąć obrazy przy użyciu okno Właściwości

1. Wybierz składnik <xref:System.Windows.Forms.ImageList> lub Dodaj go do formularza.

2. W okno Właściwości kliknij przycisk wielokropka (![przycisk wielokropka (...) w okno Właściwości programu Visual Studio.](./media/visual-studio-ellipsis-button.png)) obok właściwości <xref:System.Windows.Forms.ImageList.Images%2A>.

3. W **edytorze kolekcji obrazów**kliknij pozycję **Dodaj** lub **Usuń** , aby dodać lub usunąć obrazy z listy.

### <a name="to-add-or-remove-images-using-the-smart-tag"></a>Aby dodać lub usunąć obrazy przy użyciu tagu inteligentnego

1. Wybierz składnik <xref:System.Windows.Forms.ImageList> lub Dodaj go do formularza.

2. Kliknij symbol akcji projektanta (![Mała czarna strzałka](./media/designer-actions-glyph.gif))

3. W oknie dialogowym **ImageList Tasks (zadania** ) wybierz pozycję **Wybierz obrazy**.

4. W **edytorze kolekcji obrazów** kliknij pozycję **Dodaj** lub **Usuń** , aby dodać lub usunąć obrazy z listy.

## <a name="see-also"></a>Zobacz też

- [Obrazy, mapy bitowe i metapliki](../advanced/images-bitmaps-and-metafiles.md)
- [Przewodnik: wykonywanie typowych zadań przy użyciu akcji projektanta](perform-common-tasks-design-actions.md)
- [ImageList, składnik](imagelist-component-windows-forms.md)

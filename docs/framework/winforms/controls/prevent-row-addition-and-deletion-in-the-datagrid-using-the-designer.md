---
title: 'Instrukcje: zapobieganie dodawaniu i usuwaniu rzędów do kontrolki DataGridView formularzy systemu Windows przy użyciu narzędzia Projektant'
ms.date: 03/30/2017
helpviewer_keywords:
- DataGridView control [Windows Forms], preventing row addition or deletion
ms.assetid: a17722bd-9400-41e6-8dcc-c9c151f0a749
ms.openlocfilehash: 9f78068597edb616017876c9c72b01d44111f6f0
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/08/2019
ms.locfileid: "59220555"
---
# <a name="how-to-prevent-row-addition-and-deletion-in-the-windows-forms-datagridview-control-using-the-designer"></a>Instrukcje: zapobieganie dodawaniu i usuwaniu rzędów do kontrolki DataGridView formularzy systemu Windows przy użyciu narzędzia Projektant
Czasami można uniemożliwić użytkownikom wprowadzanie nowych wierszy danych lub usunięcie istniejących wierszy w swojej <xref:System.Windows.Forms.DataGridView> kontroli. Nowe wiersze są wprowadzane w specjalnych wiersza dla nowych rekordów w dolnej części kontrolki. Po wyłączeniu wierszy wiersza dla nowych rekordów nie jest wyświetlana. Formant może następnie wprowadzić całkowicie tylko do odczytu, wyłączając usunięcia wiersza i edytowanie komórki.  
  
 Poniższa procedura wymaga **aplikacji Windows** projektu za pomocą zawierający formularz <xref:System.Windows.Forms.DataGridView> kontroli. Aby uzyskać informacje o konfigurowaniu taki projekt, zobacz [jak: Utwórz projekt aplikacji Windows Forms](/visualstudio/ide/step-1-create-a-windows-forms-application-project) i [jak: Dodawanie formantów do formularzy Windows Forms](how-to-add-controls-to-windows-forms.md).  
  
> [!NOTE]
>  Okna dialogowe i polecenia menu mogą się różnić od tych opisanych w Pomocy, w zależności od ustawień aktywnych lub wydania. Aby zmienić swoje ustawienia, wybierz opcję **Import i eksport ustawień** na **narzędzia** menu. Aby uzyskać więcej informacji, zobacz [personalizowanie środowiska IDE programu Visual Studio](/visualstudio/ide/personalizing-the-visual-studio-ide).  
  
### <a name="to-prevent-row-addition-and-deletion"></a>Aby zapobiec wierszy i usuwanie  
  
-   Kliknij symbol tagu inteligentnego (![symbol tagu inteligentnego](./media/vs-winformsmttagglyph.gif "VS_WinFormSmtTagGlyph")) w prawym górnym rogu <xref:System.Windows.Forms.DataGridView> sterowania, a następnie wyczyść **Włącz dodawanie** i **Włącz usuwanie** pola wyboru.  
  
    > [!NOTE]
    >  Aby sprawić, że formant całkowicie tylko do odczytu, wyczyść **Włącz edytowanie** również pole wyboru.  
  
## <a name="see-also"></a>Zobacz także

- <xref:System.Windows.Forms.DataGridView>
- <xref:System.Windows.Forms.DataGridView.AllowUserToAddRows%2A?displayProperty=nameWithType>
- [Instrukcje: Utwórz projekt aplikacji Windows Forms](/visualstudio/ide/step-1-create-a-windows-forms-application-project)
- [Instrukcje: dodawanie kontrolek do formularzy systemu Windows](how-to-add-controls-to-windows-forms.md)

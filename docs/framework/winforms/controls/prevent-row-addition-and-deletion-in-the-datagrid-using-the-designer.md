---
title: "Porady: zapobieganie dodawaniu i usuwaniu rzędów do formantu DataGridView formularzy systemu Windows przy użyciu narzędzia Projektant"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: DataGridView control [Windows Forms], preventing row addition or deletion
ms.assetid: a17722bd-9400-41e6-8dcc-c9c151f0a749
caps.latest.revision: "11"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: b7671c3629830de871585dacc1afa89dde14ec50
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-prevent-row-addition-and-deletion-in-the-windows-forms-datagridview-control-using-the-designer"></a>Porady: zapobieganie dodawaniu i usuwaniu rzędów do formantu DataGridView formularzy systemu Windows przy użyciu narzędzia Projektant
Czasami można uniemożliwić użytkownikom wprowadzanie nowych wierszy danych lub usunięcie istniejących wierszy w Twojej <xref:System.Windows.Forms.DataGridView> formantu. Nowe wiersze są wprowadzane w wierszu specjalne dla nowych rekordów w dolnej części kontrolki. Po wyłączeniu dodawaniu wiersza dla nowych rekordów nie jest wyświetlana. Następnie można wprowadzić kontrolki całkowicie tylko do odczytu przez wyłączenie usunięcia wiersza i edycja komórki.  
  
 Poniższa procedura wymaga **aplikacji systemu Windows** projekt zawierający formularz <xref:System.Windows.Forms.DataGridView> formantu. Informacje o konfigurowaniu tych projektu, zobacz [jak: utworzyć projekt aplikacji systemu Windows](http://msdn.microsoft.com/en-us/b2f93fed-c635-4705-8d0e-cf079a264efa) i [porady: dodawanie formantów do formularzy systemu Windows](../../../../docs/framework/winforms/controls/how-to-add-controls-to-windows-forms.md).  
  
> [!NOTE]
>  Okna dialogowe i polecenia menu mogą się różnić od tych opisanych w Pomocy, w zależności od ustawień aktywnych lub wydania. Aby zmienić ustawienia, wybierz **Import i eksport ustawień** na **narzędzia** menu. Aby uzyskać więcej informacji, zobacz [Dostosowywanie ustawień środowiska w programie Visual Studio](http://msdn.microsoft.com/en-us/22c4debb-4e31-47a8-8f19-16f328d7dcd3).  
  
### <a name="to-prevent-row-addition-and-deletion"></a>Aby zapobiec wiersz dodawania i usuwania  
  
-   Kliknij symbol tagu inteligentnego (![symbol tagu inteligentnego](../../../../docs/framework/winforms/controls/media/vs-winformsmttagglyph.gif "VS_WinFormSmtTagGlyph")) w prawym górnym rogu <xref:System.Windows.Forms.DataGridView> kontroli, a następnie wyczyść **Włącz dodawanie** i **Włącz usuwanie** pola wyboru.  
  
    > [!NOTE]
    >  Aby całkowicie tylko do odczytu formantu, wyczyść **Włącz edytowanie** także pole wyboru.  
  
## <a name="see-also"></a>Zobacz też  
 <xref:System.Windows.Forms.DataGridView>  
 <xref:System.Windows.Forms.DataGridView.AllowUserToAddRows%2A?displayProperty=nameWithType>  
 [Porady: Tworzenie projektu aplikacji systemu Windows](http://msdn.microsoft.com/en-us/b2f93fed-c635-4705-8d0e-cf079a264efa)  
 [Instrukcje: dodawanie kontrolek do formularzy Windows Forms](../../../../docs/framework/winforms/controls/how-to-add-controls-to-windows-forms.md)

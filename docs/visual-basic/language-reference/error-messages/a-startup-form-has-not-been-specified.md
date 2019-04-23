---
title: Formularz początkowy nie został określony
ms.date: 07/20/2015
f1_keywords:
- vbrAppModel_NoStartupForm
ms.assetid: 8e04af49-4bef-49de-a7ec-e407e9873da7
ms.openlocfilehash: 2bbae640ca65c95411cae24a9506fe2076b62cba
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/18/2019
ms.locfileid: "59296475"
---
# <a name="a-startup-form-has-not-been-specified"></a>Formularz początkowy nie został określony
Aplikacja używa <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase> klasy, ale nie określa formularz początkowy.  
  
 Taka sytuacja może wystąpić, jeśli **struktury aplikacji Włącz** zaznaczono pole wyboru w Projektancie projektu, ale **formularz początkowy** nie zostanie określony. Aby uzyskać więcej informacji, zobacz [strona aplikacji, Projektant projektu (Visual Basic)](/visualstudio/ide/reference/application-page-project-designer-visual-basic).  
  
## <a name="to-correct-this-error"></a>Aby poprawić ten błąd  
  
1. Określ obiekt początkowy dla aplikacji.  
  
     Aby uzyskać więcej informacji, zobacz [strona aplikacji, Projektant projektu (Visual Basic)](/visualstudio/ide/reference/application-page-project-designer-visual-basic).  
  
2. Zastąp <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.OnCreateMainForm%2A> metodę, aby ustawić <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.MainForm%2A> właściwość formularz początkowy.  
  
## <a name="see-also"></a>Zobacz także

- <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase>
- <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.OnCreateMainForm%2A>
- <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.MainForm%2A>
- [Omówienie modelu aplikacji Visual Basic](../../../visual-basic/developing-apps/development-with-my/overview-of-the-visual-basic-application-model.md)

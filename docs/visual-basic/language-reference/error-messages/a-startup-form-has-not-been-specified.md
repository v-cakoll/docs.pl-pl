---
title: Formularz początkowy nie został określony
ms.date: 07/20/2015
f1_keywords:
- vbrAppModel_NoStartupForm
ms.assetid: 8e04af49-4bef-49de-a7ec-e407e9873da7
ms.openlocfilehash: 058deb1378ed9218274ae20c8340178f7c8fa58c
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/04/2020
ms.locfileid: "84409910"
---
# <a name="a-startup-form-has-not-been-specified"></a>Formularz początkowy nie został określony

Aplikacja używa klasy, <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase> ale nie określa formularza startowego.  
  
 Taka sytuacja może wystąpić, jeśli pole wyboru **Włącz platformę aplikacji** jest zaznaczone w projektancie projektu, ale **formularz uruchamiania** nie został określony. Aby uzyskać więcej informacji, zobacz [Strona aplikacji, Projektant projektu (Visual Basic)](/visualstudio/ide/reference/application-page-project-designer-visual-basic).  
  
## <a name="to-correct-this-error"></a>Aby poprawić ten błąd  
  
1. Określ obiekt uruchamiania dla aplikacji.  
  
     Aby uzyskać więcej informacji, zobacz [Strona aplikacji, Projektant projektu (Visual Basic)](/visualstudio/ide/reference/application-page-project-designer-visual-basic).  
  
2. Zastąp <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.OnCreateMainForm%2A> metodę, aby ustawić <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.MainForm%2A> Właściwość na formularz startowy.  
  
## <a name="see-also"></a>Zobacz też

- <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase>
- <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.OnCreateMainForm%2A>
- <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.MainForm%2A>
- [Omówienie modelu aplikacji Visual Basic](../../developing-apps/development-with-my/overview-of-the-visual-basic-application-model.md)

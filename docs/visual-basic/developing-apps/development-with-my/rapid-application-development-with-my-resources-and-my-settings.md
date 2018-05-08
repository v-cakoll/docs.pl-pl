---
title: Szybkie opracowywanie aplikacji przy użyciu My.Resources i My.Settings (Visual Basic)
ms.date: 07/20/2015
helpviewer_keywords:
- My.Settings object [Visual Basic], developing applications
- rapid application development (RAD), My.Resources
- rapid application development (RAD), My.Settings
- My.Resources object [Visual Basic], developing applications
ms.assetid: 68284ab1-b685-4814-a2a4-01ae40445ff8
ms.openlocfilehash: 808e02510d4f0a237ad4354b2edac8fa024b5f83
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="rapid-application-development-with-myresources-and-mysettings-visual-basic"></a>Szybkie opracowywanie aplikacji przy użyciu My.Resources i My.Settings (Visual Basic)
`My.Resources` Obiekt zapewnia dostęp do zasobów aplikacji i pozwala dynamicznie pobrać zasobów dla aplikacji.  
  
## <a name="retrieving-resources"></a>Pobieranie zasobów  
 Liczba zasobów, takich jak pliki dźwiękowe, ikony, obrazy i ciągi mogą zostać pobrane za pośrednictwem `My.Resources` obiektu. Na przykład można uzyskać dostępu do plików specyficzne dla kultury zasobów aplikacji. Poniższy przykład przedstawia ikonę w postaci ikony o nazwie `Form1Icon` przechowywane w pliku zasobów aplikacji.  
  
 [!code-vb[VbVbcnMy#7](../../../visual-basic/developing-apps/development-with-my/codesnippet/VisualBasic/rapid-application-development-with-my-resources-and-my-settings_1.vb)]  
  
 `My.Resources` Obiekt ujawnia tylko zasoby globalne. Nie ma dostępu do plików zasobów skojarzonych z formularzami. W formularzu musi uzyskiwać dostęp do zasobów formularza.  
  
 Podobnie `My.Settings` obiektu zapewnia dostęp do ustawień aplikacji i pozwala na dynamicznie przechowywać i pobierać ustawienia właściwości i inne informacje dotyczące aplikacji. Aby uzyskać więcej informacji, zobacz [My.resources — obiekt](../../../visual-basic/language-reference/objects/my-resources-object.md) i [My.Settings — obiekt](../../../visual-basic/language-reference/objects/my-settings-object.md).  
  
## <a name="see-also"></a>Zobacz też  
 [My.Resources, obiekt](../../../visual-basic/language-reference/objects/my-resources-object.md)  
 [My.Settings, obiekt](../../../visual-basic/language-reference/objects/my-settings-object.md)  
 [Uzyskiwanie dostępu do ustawień aplikacji](../../../visual-basic/developing-apps/programming/app-settings/accessing-application-settings.md)

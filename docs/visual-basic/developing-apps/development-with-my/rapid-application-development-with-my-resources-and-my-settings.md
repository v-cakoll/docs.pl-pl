---
title: Szybkie opracowywanie aplikacji przy użyciu My.Resources i My.Settings (Visual Basic)
ms.date: 07/20/2015
helpviewer_keywords:
- My.Settings object [Visual Basic], developing applications
- rapid application development (RAD), My.Resources
- rapid application development (RAD), My.Settings
- My.Resources object [Visual Basic], developing applications
ms.assetid: 68284ab1-b685-4814-a2a4-01ae40445ff8
ms.openlocfilehash: 7dbb15c43d044e21c9823c4a1652b0408006e5c3
ms.sourcegitcommit: 3c1c3ba79895335ff3737934e39372555ca7d6d0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/05/2018
ms.locfileid: "43802258"
---
# <a name="rapid-application-development-with-myresources-and-mysettings-visual-basic"></a>Szybkie opracowywanie aplikacji przy użyciu My.Resources i My.Settings (Visual Basic)
`My.Resources` Obiekt zapewnia dostęp do zasobów aplikacji i pozwala dynamicznie pobrać zasobów dla aplikacji.  
  
## <a name="retrieving-resources"></a>Pobieranie zasobów  
 Liczba zasobów, takich jak pliki audio, ikony, obrazy i ciągi mogą być pobierane za pośrednictwem `My.Resources` obiektu. Na przykład można uzyskać dostęp do plików specyficzne dla kultury zasobów aplikacji. W poniższym przykładzie ustawiono ikony w postaci ikony o nazwie `Form1Icon` przechowywane w pliku zasobów aplikacji.  
  
 [!code-vb[VbVbcnMy#7](../../../visual-basic/developing-apps/development-with-my/codesnippet/VisualBasic/rapid-application-development-with-my-resources-and-my-settings_1.vb)]  
  
 `My.Resources` Obiekt udostępnia tylko zasoby globalne. Zapewnia ona dostęp do plików zasobów skojarzonych z formularzami. Należy uzyskać dostęp do zasobów formularza z formularza.  
  
 Podobnie `My.Settings` obiekt umożliwia dostęp do ustawień aplikacji i pozwala na dynamiczne przechowywanie i pobieranie ustawień właściwości i inne informacje dla aplikacji. Aby uzyskać więcej informacji, zobacz [My.resources — obiekt](../../../visual-basic/language-reference/objects/my-resources-object.md) i [My.Settings — obiekt](../../../visual-basic/language-reference/objects/my-settings-object.md).  
  
## <a name="see-also"></a>Zobacz też  
 [My.Resources, obiekt](../../../visual-basic/language-reference/objects/my-resources-object.md)  
 [My.Settings, obiekt](../../../visual-basic/language-reference/objects/my-settings-object.md)  
 [Uzyskiwanie dostępu do ustawień aplikacji](../../../visual-basic/developing-apps/programming/app-settings/index.md)

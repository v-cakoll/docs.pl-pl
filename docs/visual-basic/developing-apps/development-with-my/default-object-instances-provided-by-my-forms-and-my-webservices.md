---
title: Domyślne wystąpienia obiektu zapewniane przez My.Forms i My.WebServices (Visual Basic)
ms.date: 07/20/2015
helpviewer_keywords:
- My.WebServices object [Visual Basic], developing applications
- My.Forms object [Visual Basic], developing applications
- rapid application development (RAD), My.Forms
- rapid application development (RAD), My.WebServices
ms.assetid: de930027-9108-4f0c-b97c-5e7db4d6ef79
ms.openlocfilehash: 421995684201ec48d5e8aff9b0ed7640efd1e4b9
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33582665"
---
# <a name="default-object-instances-provided-by-myforms-and-mywebservices-visual-basic"></a>Domyślne wystąpienia obiektu zapewniane przez My.Forms i My.WebServices (Visual Basic)
[My.Forms](../../../visual-basic/language-reference/objects/my-forms-object.md) i [My.WebServices](../../../visual-basic/language-reference/objects/my-webservices-object.md) obiektów zapewnienia dostępu do formularzy, źródła danych i usług XML sieci Web używanych przez aplikację. One to robić przez zapewnienie kolekcji *domyślne wystąpień* każdego z tych obiektów.  
  
## <a name="default-instances"></a>Domyślne wystąpienia  
 Domyślne wystąpienie jest wystąpieniem klasy, która jest dostarczana przez środowisko uruchomieniowe i nie musi być zadeklarowany i wdrożyć przy użyciu `Dim` i `New` instrukcje. W poniższym przykładzie pokazano sposób może mieć zadeklarowany i utworzone wystąpienie <xref:System.Windows.Forms.Form> klasy o nazwie `Form1`, i jak jesteś teraz można uzyskać domyślnego wystąpienia tego <xref:System.Windows.Forms.Form> klasy za pomocą `My.Forms`.  
  
 [!code-vb[VbVbcnMy#5](../../../visual-basic/developing-apps/development-with-my/codesnippet/VisualBasic/default-object-instances-provided-by-my-forms-and-my-webservices_1.vb)]  
  
 [!code-vb[VbVbcnMy#6](../../../visual-basic/developing-apps/development-with-my/codesnippet/VisualBasic/default-object-instances-provided-by-my-forms-and-my-webservices_2.vb)]  
  
 `My.Forms` Obiektu zwraca kolekcję wystąpień domyślną dla każdego `Form` klasy, który istnieje w projekcie. Podobnie `My.WebServices` zawiera domyślne wystąpienie klasy serwera proxy dla każdej usługi sieci Web, że utworzono odwołanie do aplikacji.  
  
## <a name="see-also"></a>Zobacz też  
 [My.Forms, obiekt](../../../visual-basic/language-reference/objects/my-forms-object.md)  
 [My.WebServices, obiekt](../../../visual-basic/language-reference/objects/my-webservices-object.md)  
 [Jak My zależy od typu projektu](../../../visual-basic/developing-apps/development-with-my/how-my-depends-on-project-type.md)

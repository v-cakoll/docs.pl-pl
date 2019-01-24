---
title: Domyślne wystąpienia obiektu zapewniane przez My.Forms i My.WebServices (Visual Basic)
ms.date: 07/20/2015
helpviewer_keywords:
- My.WebServices object [Visual Basic], developing applications
- My.Forms object [Visual Basic], developing applications
- rapid application development (RAD), My.Forms
- rapid application development (RAD), My.WebServices
ms.assetid: de930027-9108-4f0c-b97c-5e7db4d6ef79
ms.openlocfilehash: 9285e88e3dc9fd8b3731416b1c40811188d6a33d
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54563603"
---
# <a name="default-object-instances-provided-by-myforms-and-mywebservices-visual-basic"></a>Domyślne wystąpienia obiektu zapewniane przez My.Forms i My.WebServices (Visual Basic)
[My.Forms](../../../visual-basic/language-reference/objects/my-forms-object.md) i [My.WebServices](../../../visual-basic/language-reference/objects/my-webservices-object.md) obiekty zapewniają dostęp do formularzy, źródła danych i usług sieci Web XML używanych przez aplikację. Mogą to zrobić, podając kolekcji *domyślne wystąpień* każdego z tych obiektów.  
  
## <a name="default-instances"></a>Domyślne wystąpienia  
 Domyślne wystąpienie jest wystąpieniem klasy, które są dostarczane przez środowisko uruchomieniowe, a musi być zadeklarowana i tworzone przy użyciu `Dim` i `New` instrukcji. W poniższym przykładzie pokazano, jak może mieć zadeklarowana i utworzone wystąpienie <xref:System.Windows.Forms.Form> klasę o nazwie `Form1`, jak automatycznie zalogujesz się można uzyskać domyślnego wystąpienia tego <xref:System.Windows.Forms.Form> klasy za pomocą `My.Forms`.  
  
 [!code-vb[VbVbcnMy#5](../../../visual-basic/developing-apps/development-with-my/codesnippet/VisualBasic/default-object-instances-provided-by-my-forms-and-my-webservices_1.vb)]  
  
 [!code-vb[VbVbcnMy#6](../../../visual-basic/developing-apps/development-with-my/codesnippet/VisualBasic/default-object-instances-provided-by-my-forms-and-my-webservices_2.vb)]  
  
 `My.Forms` Obiektu zwraca kolekcję wystąpień domyślną dla każdego `Form` klasę, która istnieje w projekcie. Podobnie `My.WebServices` zapewnia domyślne wystąpienie klasy proxy dla każdej usługi w sieci Web, że utworzono odwołanie do aplikacji.  
  
## <a name="see-also"></a>Zobacz także
- [My.Forms, obiekt](../../../visual-basic/language-reference/objects/my-forms-object.md)
- [My.WebServices, obiekt](../../../visual-basic/language-reference/objects/my-webservices-object.md)
- [Jak My zależy od typu projektu](../../../visual-basic/developing-apps/development-with-my/how-my-depends-on-project-type.md)

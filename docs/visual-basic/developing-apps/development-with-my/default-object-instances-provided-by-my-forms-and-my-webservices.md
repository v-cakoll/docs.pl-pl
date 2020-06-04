---
title: Domyślne wystąpienia obiektu zapewniane przez My.Forms i My.WebServices
ms.date: 07/20/2015
helpviewer_keywords:
- My.WebServices object [Visual Basic], developing applications
- My.Forms object [Visual Basic], developing applications
- rapid application development (RAD), My.Forms
- rapid application development (RAD), My.WebServices
ms.assetid: de930027-9108-4f0c-b97c-5e7db4d6ef79
ms.openlocfilehash: 847724450ee2bc8bc591371f71171e8ba4ed9337
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/04/2020
ms.locfileid: "84411743"
---
# <a name="default-object-instances-provided-by-myforms-and-mywebservices-visual-basic"></a>Domyślne wystąpienia obiektu zapewniane przez My.Forms i My.WebServices (Visual Basic)

Obiekty [My. Forms](../../language-reference/objects/my-forms-object.md) i [My. WebServices](../../language-reference/objects/my-webservices-object.md) zapewniają dostęp do formularzy, źródeł danych i usług sieci Web XML używanych przez aplikację. W tym celu należy podać kolekcje *wystąpień domyślnych* każdego z tych obiektów.  
  
## <a name="default-instances"></a>Wystąpienia domyślne  

 Wystąpienie domyślne to wystąpienie klasy dostarczonej przez środowisko uruchomieniowe, które nie musi być zadeklarowane i tworzone przy użyciu `Dim` `New` instrukcji i. Poniższy przykład demonstruje, jak zostało zadeklarowane i wystąpienie wystąpienia <xref:System.Windows.Forms.Form> klasy o nazwie `Form1` i jak teraz można uzyskać domyślne wystąpienie tej <xref:System.Windows.Forms.Form> klasy przez `My.Forms` .  
  
 [!code-vb[VbVbcnMy#5](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnMy/VB/Class1.vb#5)]  
  
 [!code-vb[VbVbcnMy#6](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnMy/VB/Class1.vb#6)]  
  
 `My.Forms`Obiekt zwraca kolekcję wystąpień domyślnych dla każdej `Form` klasy, która istnieje w projekcie. Podobnie, program `My.WebServices` udostępnia domyślne wystąpienie klasy proxy dla każdej usługi sieci Web, w której utworzono odwołanie do aplikacji.  
  
## <a name="see-also"></a>Zobacz też

- [My.Forms — Obiekt](../../language-reference/objects/my-forms-object.md)
- [My.WebServices — Obiekt](../../language-reference/objects/my-webservices-object.md)
- [Jak My zależy od typu projektu](how-my-depends-on-project-type.md)

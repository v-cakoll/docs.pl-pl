---
title: Domyślne wystąpienia obiektu zapewniane przez My.Forms i My.WebServices
ms.date: 07/20/2015
helpviewer_keywords:
- My.WebServices object [Visual Basic], developing applications
- My.Forms object [Visual Basic], developing applications
- rapid application development (RAD), My.Forms
- rapid application development (RAD), My.WebServices
ms.assetid: de930027-9108-4f0c-b97c-5e7db4d6ef79
ms.openlocfilehash: 141f2f5f98499498d3c6732f7ae8d0abe6259ed9
ms.sourcegitcommit: 45c8eed045779b70a47b23169897459d0323dc89
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/18/2020
ms.locfileid: "84990248"
---
# <a name="default-object-instances-provided-by-myforms-and-mywebservices-visual-basic"></a>Domyślne wystąpienia obiektu zapewniane przez My.Forms i My.WebServices (Visual Basic)

Obiekty [My. Forms](../../language-reference/objects/my-forms-object.md) i [My. WebServices](../../language-reference/objects/my-webservices-object.md) zapewniają dostęp do formularzy, źródeł danych i usług sieci Web XML używanych przez aplikację. Zapewniają dostęp za poorednictwem kolekcji *wystąpień domyślnych* każdego z tych obiektów.  
  
## <a name="default-instances"></a>Wystąpienia domyślne  

 Wystąpienie domyślne to wystąpienie klasy dostarczonej przez środowisko uruchomieniowe, które nie musi być zadeklarowane i tworzone przy użyciu `Dim` `New` instrukcji i. Poniższy przykład demonstruje, jak zostało zadeklarowane i wystąpienie wystąpienia <xref:System.Windows.Forms.Form> klasy o nazwie `Form1` i jak teraz można uzyskać domyślne wystąpienie tej <xref:System.Windows.Forms.Form> klasy przez `My.Forms` .  
  
 [!code-vb[VbVbcnMy#5](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnMy/VB/Class1.vb#5)]  
  
 [!code-vb[VbVbcnMy#6](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnMy/VB/Class1.vb#6)]  
  
 `My.Forms`Obiekt zwraca kolekcję wystąpień domyślnych dla każdej `Form` klasy, która istnieje w projekcie. Podobnie, program `My.WebServices` udostępnia domyślne wystąpienie klasy proxy dla każdej usługi sieci Web, w której utworzono odwołanie do aplikacji.  
  
## <a name="see-also"></a>Zobacz też

- [My.Forms — Obiekt](../../language-reference/objects/my-forms-object.md)
- [My.WebServices — Obiekt](../../language-reference/objects/my-webservices-object.md)
- [Jak My zależy od typu projektu](how-my-depends-on-project-type.md)

---
title: Domyślne wystąpienia obiektu zapewniane przez My.Forms i My.WebServices
ms.date: 07/20/2015
helpviewer_keywords:
- My.WebServices object [Visual Basic], developing applications
- My.Forms object [Visual Basic], developing applications
- rapid application development (RAD), My.Forms
- rapid application development (RAD), My.WebServices
ms.assetid: de930027-9108-4f0c-b97c-5e7db4d6ef79
ms.openlocfilehash: d06df4bd023892429b2aaefdd624398a6546d06d
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/22/2019
ms.locfileid: "74330208"
---
# <a name="default-object-instances-provided-by-myforms-and-mywebservices-visual-basic"></a>Domyślne wystąpienia obiektu zapewniane przez My.Forms i My.WebServices (Visual Basic)

Obiekty [My. Forms](../../../visual-basic/language-reference/objects/my-forms-object.md) i [My. WebServices](../../../visual-basic/language-reference/objects/my-webservices-object.md) zapewniają dostęp do formularzy, źródeł danych i usług sieci Web XML używanych przez aplikację. W tym celu należy podać kolekcje *wystąpień domyślnych* każdego z tych obiektów.  
  
## <a name="default-instances"></a>Wystąpienia domyślne  

 Wystąpienie domyślne to wystąpienie klasy dostarczonej przez środowisko uruchomieniowe, które nie musi być deklarowane i tworzone przy użyciu instrukcji `Dim` i `New`. Poniższy przykład demonstruje, jak zostało zadeklarowane i wystąpienie wystąpienia klasy <xref:System.Windows.Forms.Form> o nazwie `Form1`i jak teraz można uzyskać domyślne wystąpienie tej klasy <xref:System.Windows.Forms.Form> za pomocą `My.Forms`.  
  
 [!code-vb[VbVbcnMy#5](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnMy/VB/Class1.vb#5)]  
  
 [!code-vb[VbVbcnMy#6](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnMy/VB/Class1.vb#6)]  
  
 Obiekt `My.Forms` zwraca kolekcję wystąpień domyślnych dla każdej klasy `Form`, która istnieje w projekcie. Podobnie `My.WebServices` zapewnia domyślne wystąpienie klasy proxy dla każdej usługi sieci Web, w której utworzono odwołanie do aplikacji.  
  
## <a name="see-also"></a>Zobacz także

- [My.Forms, obiekt](../../../visual-basic/language-reference/objects/my-forms-object.md)
- [My.WebServices, obiekt](../../../visual-basic/language-reference/objects/my-webservices-object.md)
- [Jak My zależy od typu projektu](../../../visual-basic/developing-apps/development-with-my/how-my-depends-on-project-type.md)

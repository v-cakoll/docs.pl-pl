---
title: 'Instrukcje: Umożliwianie serializacji jednostek'
ms.date: 03/30/2017
ms.assetid: a6c5bf6e-064a-4f77-b74c-76b3a5dec309
ms.openlocfilehash: 40a0b4d5a49f88af1bedcbefdd117f6c000b791d
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/07/2019
ms.locfileid: "70793565"
---
# <a name="how-to-make-entities-serializable"></a>Instrukcje: Umożliwianie serializacji jednostek
Jednostki można serializować podczas generowania kodu. Klasy jednostek są dekoracyjne <xref:System.Runtime.Serialization.DataContractAttribute> i są kolumnami <xref:System.Runtime.Serialization.DataMemberAttribute> z atrybutem.  
  
 Deweloperzy korzystający z programu Visual Studio mogą w tym celu używać Object Relational Designer.  
  
 Jeśli używasz narzędzia wiersza polecenia SQLMetal, użyj opcji **/Serialization** z `unidirectional` argumentem. Aby uzyskać więcej informacji, zobacz [SQLMetal. exe (Narzędzie generowania kodu)](../../../../tools/sqlmetal-exe-code-generation-tool.md).  
  
## <a name="example"></a>Przykład  
 Następujące wiersze poleceń SQLMetal tworzą pliki, które mają możliwe do serializacji jednostki.  
  
```  
sqlmetal /code:nwserializable.vb /language:vb "c:\northwnd.mdf" /sprocs /functions /pluralize /serialization:unidirectional  
```  
  
```  
sqlmetal /code:nwserializable.cs /language:csharp "c:\northwnd.mdf" /sprocs /functions /pluralize /serialization:unidirectional  
```  
  
## <a name="see-also"></a>Zobacz także

- [Serializacja](serialization.md)
- [Tworzenie modelu obiektu](creating-the-object-model.md)

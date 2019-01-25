---
title: 'Instrukcje: Umożliwianie serializacji jednostek'
ms.date: 03/30/2017
ms.assetid: a6c5bf6e-064a-4f77-b74c-76b3a5dec309
ms.openlocfilehash: 9b4ff81b4a779b474097de1a69e65f4864e08691
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54604229"
---
# <a name="how-to-make-entities-serializable"></a>Instrukcje: Umożliwianie serializacji jednostek
Jednostki można wprowadzić do serializacji, podczas generowania kodu. Klas jednostek są ozdobione <xref:System.Runtime.Serialization.DataContractAttribute> atrybutu i kolumny z <xref:System.Runtime.Serialization.DataMemberAttribute> atrybutu.  
  
 Za pomocą programu Visual Studio deweloperzy mogą używać [!INCLUDE[vs_ordesigner_long](../../../../../../includes/vs-ordesigner-long-md.md)] do tego celu.  
  
 Jeśli używasz narzędzia wiersza polecenia SQLMetal, użyj **/serialization** z opcją `unidirectional` argumentu. Aby uzyskać więcej informacji, zobacz [SqlMetal.exe (narzędzie generowania kodu)](../../../../../../docs/framework/tools/sqlmetal-exe-code-generation-tool.md).  
  
## <a name="example"></a>Przykład  
 Następujące wiersze polecenia SQLMetal generuje pliki, które dysponują jednostkami możliwy do serializacji.  
  
```  
sqlmetal /code:nwserializable.vb /language:vb "c:\northwnd.mdf" /sprocs /functions /pluralize /serialization:unidirectional  
```  
  
```  
sqlmetal /code:nwserializable.cs /language:csharp "c:\northwnd.mdf" /sprocs /functions /pluralize /serialization:unidirectional  
```  
  
## <a name="see-also"></a>Zobacz także
- [Serializacja](../../../../../../docs/framework/data/adonet/sql/linq/serialization.md)
- [Tworzenie modelu obiektu](../../../../../../docs/framework/data/adonet/sql/linq/creating-the-object-model.md)

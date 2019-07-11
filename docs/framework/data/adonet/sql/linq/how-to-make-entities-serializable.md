---
title: 'Instrukcje: Umożliwianie serializacji jednostek'
ms.date: 03/30/2017
ms.assetid: a6c5bf6e-064a-4f77-b74c-76b3a5dec309
ms.openlocfilehash: fd687ba5dce16baee063f1d3bb9521c6664988b0
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/10/2019
ms.locfileid: "67743279"
---
# <a name="how-to-make-entities-serializable"></a>Instrukcje: Umożliwianie serializacji jednostek
Jednostki można wprowadzić do serializacji, podczas generowania kodu. Klas jednostek są ozdobione <xref:System.Runtime.Serialization.DataContractAttribute> atrybutu i kolumny z <xref:System.Runtime.Serialization.DataMemberAttribute> atrybutu.  
  
 Deweloperzy korzystający z programu Visual Studio można użyć Object Relational Designer w tym celu.  
  
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

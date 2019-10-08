---
title: 'Instrukcje: Tworzenie obiektów do serializacji'
ms.date: 03/30/2017
ms.assetid: a6c5bf6e-064a-4f77-b74c-76b3a5dec309
ms.openlocfilehash: 5e9d078ed2daacfa48b09693f533e9aade613281
ms.sourcegitcommit: eff6adb61852369ab690f3f047818c90580e7eb1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/07/2019
ms.locfileid: "72002714"
---
# <a name="how-to-make-entities-serializable"></a>Instrukcje: Tworzenie obiektów do serializacji
Jednostki można serializować podczas generowania kodu. Klasy jednostek są uzupełnione atrybutem <xref:System.Runtime.Serialization.DataContractAttribute> i kolumnami z atrybutem <xref:System.Runtime.Serialization.DataMemberAttribute>.  
  
 Deweloperzy korzystający z programu Visual Studio mogą w tym celu używać Object Relational Designer.  
  
 Jeśli używasz narzędzia wiersza polecenia SQLMetal, użyj opcji **/Serialization** z argumentem `unidirectional`. Aby uzyskać więcej informacji, zobacz [SQLMetal. exe (Narzędzie generowania kodu)](../../../../tools/sqlmetal-exe-code-generation-tool.md).  
  
## <a name="example"></a>Przykład  
 Następujące wiersze poleceń SQLMetal tworzą pliki, które mają możliwe do serializacji jednostki.  
  
```console  
sqlmetal /code:nwserializable.vb /language:vb "c:\northwnd.mdf" /sprocs /functions /pluralize /serialization:unidirectional  
```  
  
```console  
sqlmetal /code:nwserializable.cs /language:csharp "c:\northwnd.mdf" /sprocs /functions /pluralize /serialization:unidirectional  
```  
  
## <a name="see-also"></a>Zobacz także

- [Serializacja](serialization.md)
- [Tworzenie modelu obiektu](creating-the-object-model.md)

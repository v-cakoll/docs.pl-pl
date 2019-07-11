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
# <a name="how-to-make-entities-serializable"></a><span data-ttu-id="dbbf0-102">Instrukcje: Umożliwianie serializacji jednostek</span><span class="sxs-lookup"><span data-stu-id="dbbf0-102">How to: Make Entities Serializable</span></span>
<span data-ttu-id="dbbf0-103">Jednostki można wprowadzić do serializacji, podczas generowania kodu.</span><span class="sxs-lookup"><span data-stu-id="dbbf0-103">You can make entities serializable when you generate your code.</span></span> <span data-ttu-id="dbbf0-104">Klas jednostek są ozdobione <xref:System.Runtime.Serialization.DataContractAttribute> atrybutu i kolumny z <xref:System.Runtime.Serialization.DataMemberAttribute> atrybutu.</span><span class="sxs-lookup"><span data-stu-id="dbbf0-104">Entity classes are decorated with the <xref:System.Runtime.Serialization.DataContractAttribute> attribute, and columns with the <xref:System.Runtime.Serialization.DataMemberAttribute> attribute.</span></span>  
  
 <span data-ttu-id="dbbf0-105">Deweloperzy korzystający z programu Visual Studio można użyć Object Relational Designer w tym celu.</span><span class="sxs-lookup"><span data-stu-id="dbbf0-105">Developers using Visual Studio can use the Object Relational Designer for this purpose.</span></span>  
  
 <span data-ttu-id="dbbf0-106">Jeśli używasz narzędzia wiersza polecenia SQLMetal, użyj **/serialization** z opcją `unidirectional` argumentu.</span><span class="sxs-lookup"><span data-stu-id="dbbf0-106">If you are using the SQLMetal command-line tool, use the **/serialization** option with the `unidirectional` argument.</span></span> <span data-ttu-id="dbbf0-107">Aby uzyskać więcej informacji, zobacz [SqlMetal.exe (narzędzie generowania kodu)](../../../../../../docs/framework/tools/sqlmetal-exe-code-generation-tool.md).</span><span class="sxs-lookup"><span data-stu-id="dbbf0-107">For more information, see [SqlMetal.exe (Code Generation Tool)](../../../../../../docs/framework/tools/sqlmetal-exe-code-generation-tool.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="dbbf0-108">Przykład</span><span class="sxs-lookup"><span data-stu-id="dbbf0-108">Example</span></span>  
 <span data-ttu-id="dbbf0-109">Następujące wiersze polecenia SQLMetal generuje pliki, które dysponują jednostkami możliwy do serializacji.</span><span class="sxs-lookup"><span data-stu-id="dbbf0-109">The following SQLMetal command lines produce files that have serializable entities.</span></span>  
  
```  
sqlmetal /code:nwserializable.vb /language:vb "c:\northwnd.mdf" /sprocs /functions /pluralize /serialization:unidirectional  
```  
  
```  
sqlmetal /code:nwserializable.cs /language:csharp "c:\northwnd.mdf" /sprocs /functions /pluralize /serialization:unidirectional  
```  
  
## <a name="see-also"></a><span data-ttu-id="dbbf0-110">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="dbbf0-110">See also</span></span>

- [<span data-ttu-id="dbbf0-111">Serializacja</span><span class="sxs-lookup"><span data-stu-id="dbbf0-111">Serialization</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/serialization.md)
- [<span data-ttu-id="dbbf0-112">Tworzenie modelu obiektu</span><span class="sxs-lookup"><span data-stu-id="dbbf0-112">Creating the Object Model</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/creating-the-object-model.md)

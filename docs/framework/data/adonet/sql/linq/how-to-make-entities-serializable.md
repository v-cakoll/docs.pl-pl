---
title: 'Instrukcje: Umożliwianie serializacji jednostek'
ms.date: 03/30/2017
ms.assetid: a6c5bf6e-064a-4f77-b74c-76b3a5dec309
ms.openlocfilehash: bbe40ec448bef5f62d4182d96f82c6308639e27f
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/18/2019
ms.locfileid: "59086770"
---
# <a name="how-to-make-entities-serializable"></a><span data-ttu-id="98266-102">Instrukcje: Umożliwianie serializacji jednostek</span><span class="sxs-lookup"><span data-stu-id="98266-102">How to: Make Entities Serializable</span></span>
<span data-ttu-id="98266-103">Jednostki można wprowadzić do serializacji, podczas generowania kodu.</span><span class="sxs-lookup"><span data-stu-id="98266-103">You can make entities serializable when you generate your code.</span></span> <span data-ttu-id="98266-104">Klas jednostek są ozdobione <xref:System.Runtime.Serialization.DataContractAttribute> atrybutu i kolumny z <xref:System.Runtime.Serialization.DataMemberAttribute> atrybutu.</span><span class="sxs-lookup"><span data-stu-id="98266-104">Entity classes are decorated with the <xref:System.Runtime.Serialization.DataContractAttribute> attribute, and columns with the <xref:System.Runtime.Serialization.DataMemberAttribute> attribute.</span></span>  
  
 <span data-ttu-id="98266-105">Za pomocą programu Visual Studio deweloperzy mogą używać [!INCLUDE[vs_ordesigner_long](../../../../../../includes/vs-ordesigner-long-md.md)] do tego celu.</span><span class="sxs-lookup"><span data-stu-id="98266-105">Developers using Visual Studio can use the [!INCLUDE[vs_ordesigner_long](../../../../../../includes/vs-ordesigner-long-md.md)] for this purpose.</span></span>  
  
 <span data-ttu-id="98266-106">Jeśli używasz narzędzia wiersza polecenia SQLMetal, użyj **/serialization** z opcją `unidirectional` argumentu.</span><span class="sxs-lookup"><span data-stu-id="98266-106">If you are using the SQLMetal command-line tool, use the **/serialization** option with the `unidirectional` argument.</span></span> <span data-ttu-id="98266-107">Aby uzyskać więcej informacji, zobacz [SqlMetal.exe (narzędzie generowania kodu)](../../../../../../docs/framework/tools/sqlmetal-exe-code-generation-tool.md).</span><span class="sxs-lookup"><span data-stu-id="98266-107">For more information, see [SqlMetal.exe (Code Generation Tool)](../../../../../../docs/framework/tools/sqlmetal-exe-code-generation-tool.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="98266-108">Przykład</span><span class="sxs-lookup"><span data-stu-id="98266-108">Example</span></span>  
 <span data-ttu-id="98266-109">Następujące wiersze polecenia SQLMetal generuje pliki, które dysponują jednostkami możliwy do serializacji.</span><span class="sxs-lookup"><span data-stu-id="98266-109">The following SQLMetal command lines produce files that have serializable entities.</span></span>  
  
```  
sqlmetal /code:nwserializable.vb /language:vb "c:\northwnd.mdf" /sprocs /functions /pluralize /serialization:unidirectional  
```  
  
```  
sqlmetal /code:nwserializable.cs /language:csharp "c:\northwnd.mdf" /sprocs /functions /pluralize /serialization:unidirectional  
```  
  
## <a name="see-also"></a><span data-ttu-id="98266-110">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="98266-110">See also</span></span>

- [<span data-ttu-id="98266-111">Serializacja</span><span class="sxs-lookup"><span data-stu-id="98266-111">Serialization</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/serialization.md)
- [<span data-ttu-id="98266-112">Tworzenie modelu obiektu</span><span class="sxs-lookup"><span data-stu-id="98266-112">Creating the Object Model</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/creating-the-object-model.md)

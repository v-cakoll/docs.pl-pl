---
title: 'Porady: należy do serializacji jednostek'
ms.date: 03/30/2017
ms.assetid: a6c5bf6e-064a-4f77-b74c-76b3a5dec309
ms.openlocfilehash: c3b877df9707e0f98dbc2238d910842649def07f
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="how-to-make-entities-serializable"></a><span data-ttu-id="beeb3-102">Porady: należy do serializacji jednostek</span><span class="sxs-lookup"><span data-stu-id="beeb3-102">How to: Make Entities Serializable</span></span>
<span data-ttu-id="beeb3-103">Możesz wprowadzić jednostek serializacji, podczas generowania kodu.</span><span class="sxs-lookup"><span data-stu-id="beeb3-103">You can make entities serializable when you generate your code.</span></span> <span data-ttu-id="beeb3-104">Klasy jednostki są oznaczone <xref:System.Runtime.Serialization.DataContractAttribute> atrybutu i kolumny z <xref:System.Runtime.Serialization.DataMemberAttribute> atrybutu.</span><span class="sxs-lookup"><span data-stu-id="beeb3-104">Entity classes are decorated with the <xref:System.Runtime.Serialization.DataContractAttribute> attribute, and columns with the <xref:System.Runtime.Serialization.DataMemberAttribute> attribute.</span></span>  
  
 <span data-ttu-id="beeb3-105">Za pomocą programu Visual Studio deweloperzy mogą używać [!INCLUDE[vs_ordesigner_long](../../../../../../includes/vs-ordesigner-long-md.md)] w tym celu.</span><span class="sxs-lookup"><span data-stu-id="beeb3-105">Developers using Visual Studio can use the [!INCLUDE[vs_ordesigner_long](../../../../../../includes/vs-ordesigner-long-md.md)] for this purpose.</span></span>  
  
 <span data-ttu-id="beeb3-106">Jeśli używasz narzędzia wiersza polecenia SQLMetal, użyj **/serialization** opcję z `unidirectional` argumentu.</span><span class="sxs-lookup"><span data-stu-id="beeb3-106">If you are using the SQLMetal command-line tool, use the **/serialization** option with the `unidirectional` argument.</span></span> <span data-ttu-id="beeb3-107">Aby uzyskać więcej informacji, zobacz [SqlMetal.exe (narzędzie generowania kodu)](../../../../../../docs/framework/tools/sqlmetal-exe-code-generation-tool.md).</span><span class="sxs-lookup"><span data-stu-id="beeb3-107">For more information, see [SqlMetal.exe (Code Generation Tool)](../../../../../../docs/framework/tools/sqlmetal-exe-code-generation-tool.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="beeb3-108">Przykład</span><span class="sxs-lookup"><span data-stu-id="beeb3-108">Example</span></span>  
 <span data-ttu-id="beeb3-109">Następujące wiersze polecenia SQLMetal tworzy pliki, których podmioty możliwy do serializacji.</span><span class="sxs-lookup"><span data-stu-id="beeb3-109">The following SQLMetal command lines produce files that have serializable entities.</span></span>  
  
```  
sqlmetal /code:nwserializable.vb /language:vb "c:\northwnd.mdf" /sprocs /functions /pluralize /serialization:unidirectional  
```  
  
```  
sqlmetal /code:nwserializable.cs /language:csharp "c:\northwnd.mdf" /sprocs /functions /pluralize /serialization:unidirectional  
```  
  
## <a name="see-also"></a><span data-ttu-id="beeb3-110">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="beeb3-110">See Also</span></span>  
 [<span data-ttu-id="beeb3-111">Serializacja</span><span class="sxs-lookup"><span data-stu-id="beeb3-111">Serialization</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/serialization.md)  
 [<span data-ttu-id="beeb3-112">Tworzenie modelu obiektu</span><span class="sxs-lookup"><span data-stu-id="beeb3-112">Creating the Object Model</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/creating-the-object-model.md)

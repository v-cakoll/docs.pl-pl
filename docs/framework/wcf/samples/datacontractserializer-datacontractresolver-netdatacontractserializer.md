---
title: Używanie elementów DataContractSerializer i DataContractResolver do udostępniania funkcji elementu NetDataContractSerializer
ms.date: 03/30/2017
ms.assetid: 1376658f-f695-45f7-a7e0-94664e9619ff
ms.openlocfilehash: b86ac822e7ce7f0b18962fe48adbb1c26d7259dd
ms.sourcegitcommit: efff8f331fd9467f093f8ab8d23a203d6ecb5b60
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/01/2018
ms.locfileid: "43394302"
---
# <a name="using-datacontractserializer-and-datacontractresolver-to-provide-the-functionality-of-netdatacontractserializer"></a><span data-ttu-id="f3ac2-102">Używanie elementów DataContractSerializer i DataContractResolver do udostępniania funkcji elementu NetDataContractSerializer</span><span class="sxs-lookup"><span data-stu-id="f3ac2-102">Using DataContractSerializer and DataContractResolver to Provide the Functionality of NetDataContractSerializer</span></span>
<span data-ttu-id="f3ac2-103">W tym przykładzie przedstawiono sposób użycia <xref:System.Runtime.Serialization.DataContractSerializer> odpowiednimi <xref:System.Runtime.Serialization.DataContractResolver> zapewnia taką samą funkcjonalność jak <xref:System.Runtime.Serialization.NetDataContractSerializer>.</span><span class="sxs-lookup"><span data-stu-id="f3ac2-103">This sample demonstrates how the use of <xref:System.Runtime.Serialization.DataContractSerializer> with an appropriate <xref:System.Runtime.Serialization.DataContractResolver> provides the same functionality as <xref:System.Runtime.Serialization.NetDataContractSerializer>.</span></span> <span data-ttu-id="f3ac2-104">W tym przykładzie przedstawiono sposób tworzenia odpowiednie <xref:System.Runtime.Serialization.DataContractResolver> oraz jak je dodać <xref:System.Runtime.Serialization.DataContractSerializer>.</span><span class="sxs-lookup"><span data-stu-id="f3ac2-104">This sample shows how to create the appropriate <xref:System.Runtime.Serialization.DataContractResolver> and how to add it to the <xref:System.Runtime.Serialization.DataContractSerializer>.</span></span>  
  
## <a name="sample-details"></a><span data-ttu-id="f3ac2-105">Przykład szczegółów</span><span class="sxs-lookup"><span data-stu-id="f3ac2-105">Sample details</span></span>  
 <span data-ttu-id="f3ac2-106"><xref:System.Runtime.Serialization.NetDataContractSerializer> różni się od <xref:System.Runtime.Serialization.DataContractSerializer> w jednym ze sposobów ważne: <xref:System.Runtime.Serialization.NetDataContractSerializer> zawiera informacje o typie CLR w serializacji XML, a <xref:System.Runtime.Serialization.DataContractSerializer> nie.</span><span class="sxs-lookup"><span data-stu-id="f3ac2-106"><xref:System.Runtime.Serialization.NetDataContractSerializer> differs from <xref:System.Runtime.Serialization.DataContractSerializer> in one important way: <xref:System.Runtime.Serialization.NetDataContractSerializer> includes CLR type information in the serialized XML, whereas <xref:System.Runtime.Serialization.DataContractSerializer> does not.</span></span> <span data-ttu-id="f3ac2-107">W związku z tym <xref:System.Runtime.Serialization.NetDataContractSerializer> mogą służyć tylko wtedy, gdy zarówno serializacji i deserializacji kończy się udostępniać te same typy CLR.</span><span class="sxs-lookup"><span data-stu-id="f3ac2-107">Therefore, <xref:System.Runtime.Serialization.NetDataContractSerializer> can be used only if both the serializing and deserializing ends share the same CLR types.</span></span> <span data-ttu-id="f3ac2-108">Jednak zaleca się używanie <xref:System.Runtime.Serialization.DataContractSerializer> ponieważ jego wydajność, większą niż <xref:System.Runtime.Serialization.NetDataContractSerializer>.</span><span class="sxs-lookup"><span data-stu-id="f3ac2-108">However, it is recommended to use <xref:System.Runtime.Serialization.DataContractSerializer> because its performance is better than <xref:System.Runtime.Serialization.NetDataContractSerializer>.</span></span> <span data-ttu-id="f3ac2-109">Można zmienić informacje, które jest serializowana we <xref:System.Runtime.Serialization.DataContractSerializer> , dodając <xref:System.Runtime.Serialization.DataContractResolver> do niego.</span><span class="sxs-lookup"><span data-stu-id="f3ac2-109">You can change the information that is serialized in <xref:System.Runtime.Serialization.DataContractSerializer> by adding a <xref:System.Runtime.Serialization.DataContractResolver> to it.</span></span>  
  
 <span data-ttu-id="f3ac2-110">Ten przykład obejmuje dwa projekty.</span><span class="sxs-lookup"><span data-stu-id="f3ac2-110">This sample consists of two projects.</span></span> <span data-ttu-id="f3ac2-111">Używa pierwszego projektu <xref:System.Runtime.Serialization.NetDataContractSerializer> do serializacji obiektu.</span><span class="sxs-lookup"><span data-stu-id="f3ac2-111">The first project uses <xref:System.Runtime.Serialization.NetDataContractSerializer> to serialize an object.</span></span> <span data-ttu-id="f3ac2-112">Drugi projekt używa <xref:System.Runtime.Serialization.DataContractSerializer> z <xref:System.Runtime.Serialization.DataContractResolver> zapewnienie taką samą funkcjonalność jak pierwszy projekt.</span><span class="sxs-lookup"><span data-stu-id="f3ac2-112">The second project uses <xref:System.Runtime.Serialization.DataContractSerializer> with a <xref:System.Runtime.Serialization.DataContractResolver> to provide the same functionality as the first project.</span></span>  
  
 <span data-ttu-id="f3ac2-113">Poniższy przykład kodu pokazuje implementację niestandardowej <xref:System.Runtime.Serialization.DataContractResolver> o nazwie `MyDataContractResolver` który został dodany do <xref:System.Runtime.Serialization.DataContractSerializer> w projekcie DCSwithDCR.</span><span class="sxs-lookup"><span data-stu-id="f3ac2-113">The following code example shows the implementation of a custom <xref:System.Runtime.Serialization.DataContractResolver> named `MyDataContractResolver` that is added to the <xref:System.Runtime.Serialization.DataContractSerializer> in the DCSwithDCR project.</span></span>  
  
```  
class MyDataContractResolver : DataContractResolver  
{  
    private XmlDictionary dictionary = new XmlDictionary();  
  
    public MyDataContractResolver()  
    {  
    }  
  
    // Used at deserialization  
    // Allows users to map xsi:type name to any Type   
    public override Type ResolveName(string typeName, string typeNamespace, DataContractResolver knownTypeResolver)  
    {  
        Type type = knownTypeResolver.ResolveName(typeName, typeNamespace, null);  
        if (type == null)  
        {  
            type = Type.GetType(typeName + ", " + typeNamespace);  
        }  
        return type;  
    }  
  
    // Used at serialization  
    // Maps any Type to a new xsi:type representation  
    public override void ResolveType(Type dataContractType, DataContractResolver knownTypeResolver, out XmlDictionaryString typeName, out XmlDictionaryString typeNamespace)  
    {  
        knownTypeResolver.ResolveType(dataContractType, null, out typeName, out typeNamespace);  
        if (typeName == null || typeNamespace == null)  
        {  
            XmlDictionary dictionary = new XmlDictionary();  
            typeName = dictionary.Add(dataContractType.FullName);  
            typeNamespace = dictionary.Add(dataContractType.Assembly.FullName);  
        }  
    }  
}  
```  
  
#### <a name="to-use-this-sample"></a><span data-ttu-id="f3ac2-114">Aby użyć tego przykładu</span><span class="sxs-lookup"><span data-stu-id="f3ac2-114">To use this sample</span></span>  
  
1.  <span data-ttu-id="f3ac2-115">Za pomocą [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)], otwórz plik rozwiązania DCRSample.sln.</span><span class="sxs-lookup"><span data-stu-id="f3ac2-115">Using [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)], open the DCRSample.sln solution file.</span></span>  
  
2.  <span data-ttu-id="f3ac2-116">Kliknij prawym przyciskiem myszy plik rozwiązania, a następnie wybierz **właściwości**.</span><span class="sxs-lookup"><span data-stu-id="f3ac2-116">Right-click the solution file and choose **Properties**.</span></span>  
  
3.  <span data-ttu-id="f3ac2-117">W **strony właściwości rozwiązania** okna dialogowego, w obszarze **wspólne właściwości**, **projekt startowy**, wybierz opcję **wiele projektów startowych:**.</span><span class="sxs-lookup"><span data-stu-id="f3ac2-117">In the **Solution Property Pages** dialog, under **Common Properties**, **Startup Project**, select **Multiple startup projects:**.</span></span>  
  
4.  <span data-ttu-id="f3ac2-118">Obok pozycji **DCSwithDCR** projektu, wybierz opcję **Start** z **akcji** listy rozwijanej.</span><span class="sxs-lookup"><span data-stu-id="f3ac2-118">Next to the **DCSwithDCR** project, select **Start** from the **Action** dropdown.</span></span>  
  
5.  <span data-ttu-id="f3ac2-119">Obok pozycji **NetDCS** projektu, wybierz opcję **Start** z **akcji** listy rozwijanej.</span><span class="sxs-lookup"><span data-stu-id="f3ac2-119">Next to the **NetDCS** project, select **Start** from the **Action** dropdown.</span></span>  
  
6.  <span data-ttu-id="f3ac2-120">Kliknij przycisk **OK** aby zamknąć okno dialogowe.</span><span class="sxs-lookup"><span data-stu-id="f3ac2-120">Click **OK** to close the dialog.</span></span>  
  
7.  <span data-ttu-id="f3ac2-121">Aby skompilować rozwiązanie, naciśnij klawisze CTRL + SHIFT + B.</span><span class="sxs-lookup"><span data-stu-id="f3ac2-121">To build the solution, press CTRL+SHIFT+B.</span></span>  
  
8.  <span data-ttu-id="f3ac2-122">Aby uruchomić rozwiązanie, naciśnij kombinację klawiszy CTRL + F5.</span><span class="sxs-lookup"><span data-stu-id="f3ac2-122">To run the solution, press CTRL+F5.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="f3ac2-123">Przykłady może już być zainstalowany na tym komputerze.</span><span class="sxs-lookup"><span data-stu-id="f3ac2-123">The samples may already be installed on your machine.</span></span> <span data-ttu-id="f3ac2-124">Przed kontynuowaniem sprawdź, czy są dostępne dla następującego katalogu (ustawienie domyślne).</span><span class="sxs-lookup"><span data-stu-id="f3ac2-124">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="f3ac2-125">Jeśli ten katalog nie istnieje, przejdź do strony [Windows Communication Foundation (WCF) i przykłady Windows Workflow Foundation (WF) dla platformy .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) do pobierania wszystkich Windows Communication Foundation (WCF) i [!INCLUDE[wf1](../../../../includes/wf1-md.md)] przykładów.</span><span class="sxs-lookup"><span data-stu-id="f3ac2-125">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="f3ac2-126">W tym przykładzie znajduje się w następującym katalogu.</span><span class="sxs-lookup"><span data-stu-id="f3ac2-126">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Contract\Data\NetDcSasDcSwithDCR`  
  
## <a name="see-also"></a><span data-ttu-id="f3ac2-127">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="f3ac2-127">See Also</span></span>

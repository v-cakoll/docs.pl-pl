---
title: Używanie elementów DataContractSerializer i DataContractResolver do udostępniania funkcji elementu NetDataContractSerializer
ms.date: 03/30/2017
ms.assetid: 1376658f-f695-45f7-a7e0-94664e9619ff
ms.openlocfilehash: d7102e60c8b5302d4f3bc83b356dbc7de117f57a
ms.sourcegitcommit: 581ab03291e91983459e56e40ea8d97b5189227e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/27/2019
ms.locfileid: "70039862"
---
# <a name="using-datacontractserializer-and-datacontractresolver-to-provide-the-functionality-of-netdatacontractserializer"></a><span data-ttu-id="6fa5b-102">Używanie elementów DataContractSerializer i DataContractResolver do udostępniania funkcji elementu NetDataContractSerializer</span><span class="sxs-lookup"><span data-stu-id="6fa5b-102">Using DataContractSerializer and DataContractResolver to Provide the Functionality of NetDataContractSerializer</span></span>
<span data-ttu-id="6fa5b-103">W tym przykładzie pokazano, jak korzystanie <xref:System.Runtime.Serialization.DataContractSerializer> z programu z <xref:System.Runtime.Serialization.DataContractResolver> odpowiednim zapewnia taką samą funkcjonalność <xref:System.Runtime.Serialization.NetDataContractSerializer>jak w przypadku programu.</span><span class="sxs-lookup"><span data-stu-id="6fa5b-103">This sample demonstrates how the use of <xref:System.Runtime.Serialization.DataContractSerializer> with an appropriate <xref:System.Runtime.Serialization.DataContractResolver> provides the same functionality as <xref:System.Runtime.Serialization.NetDataContractSerializer>.</span></span> <span data-ttu-id="6fa5b-104">Ten przykład pokazuje, jak utworzyć odpowiednie <xref:System.Runtime.Serialization.DataContractResolver> i jak dodać je <xref:System.Runtime.Serialization.DataContractSerializer>do.</span><span class="sxs-lookup"><span data-stu-id="6fa5b-104">This sample shows how to create the appropriate <xref:System.Runtime.Serialization.DataContractResolver> and how to add it to the <xref:System.Runtime.Serialization.DataContractSerializer>.</span></span>

## <a name="sample-details"></a><span data-ttu-id="6fa5b-105">Przykładowe szczegóły</span><span class="sxs-lookup"><span data-stu-id="6fa5b-105">Sample details</span></span>
 <span data-ttu-id="6fa5b-106"><xref:System.Runtime.Serialization.NetDataContractSerializer>różni się <xref:System.Runtime.Serialization.DataContractSerializer> od w jednym z ważnych <xref:System.Runtime.Serialization.NetDataContractSerializer> sposobów: zawiera informacje o typie CLR w serializowanym <xref:System.Runtime.Serialization.DataContractSerializer> kodzie XML, a nie.</span><span class="sxs-lookup"><span data-stu-id="6fa5b-106"><xref:System.Runtime.Serialization.NetDataContractSerializer> differs from <xref:System.Runtime.Serialization.DataContractSerializer> in one important way: <xref:System.Runtime.Serialization.NetDataContractSerializer> includes CLR type information in the serialized XML, whereas <xref:System.Runtime.Serialization.DataContractSerializer> does not.</span></span> <span data-ttu-id="6fa5b-107">W związku <xref:System.Runtime.Serialization.NetDataContractSerializer> z tym, mogą być używane tylko wtedy, gdy obie operacje serializacji i deserializacji współużytkują te same typy CLR.</span><span class="sxs-lookup"><span data-stu-id="6fa5b-107">Therefore, <xref:System.Runtime.Serialization.NetDataContractSerializer> can be used only if both the serializing and deserializing ends share the same CLR types.</span></span> <span data-ttu-id="6fa5b-108">Zaleca się jednak użycie <xref:System.Runtime.Serialization.DataContractSerializer> , ponieważ jego wydajność jest lepsza niż. <xref:System.Runtime.Serialization.NetDataContractSerializer></span><span class="sxs-lookup"><span data-stu-id="6fa5b-108">However, it is recommended to use <xref:System.Runtime.Serialization.DataContractSerializer> because its performance is better than <xref:System.Runtime.Serialization.NetDataContractSerializer>.</span></span> <span data-ttu-id="6fa5b-109">Można zmienić informacje, które są serializowane w <xref:System.Runtime.Serialization.DataContractSerializer> programie, <xref:System.Runtime.Serialization.DataContractResolver> dodając do niego.</span><span class="sxs-lookup"><span data-stu-id="6fa5b-109">You can change the information that is serialized in <xref:System.Runtime.Serialization.DataContractSerializer> by adding a <xref:System.Runtime.Serialization.DataContractResolver> to it.</span></span>

 <span data-ttu-id="6fa5b-110">Ten przykład składa się z dwóch projektów.</span><span class="sxs-lookup"><span data-stu-id="6fa5b-110">This sample consists of two projects.</span></span> <span data-ttu-id="6fa5b-111">Pierwszy projekt używa <xref:System.Runtime.Serialization.NetDataContractSerializer> do serializacji obiektu.</span><span class="sxs-lookup"><span data-stu-id="6fa5b-111">The first project uses <xref:System.Runtime.Serialization.NetDataContractSerializer> to serialize an object.</span></span> <span data-ttu-id="6fa5b-112">Drugi projekt używa <xref:System.Runtime.Serialization.DataContractSerializer> programu <xref:System.Runtime.Serialization.DataContractResolver> z programem, aby zapewnić te same funkcje co pierwszy projekt.</span><span class="sxs-lookup"><span data-stu-id="6fa5b-112">The second project uses <xref:System.Runtime.Serialization.DataContractSerializer> with a <xref:System.Runtime.Serialization.DataContractResolver> to provide the same functionality as the first project.</span></span>

 <span data-ttu-id="6fa5b-113">Poniższy przykład kodu pokazuje implementację niestandardowej <xref:System.Runtime.Serialization.DataContractResolver> o nazwie `MyDataContractResolver` <xref:System.Runtime.Serialization.DataContractSerializer> , która jest dodawana do w projekcie DCSwithDCR.</span><span class="sxs-lookup"><span data-stu-id="6fa5b-113">The following code example shows the implementation of a custom <xref:System.Runtime.Serialization.DataContractResolver> named `MyDataContractResolver` that is added to the <xref:System.Runtime.Serialization.DataContractSerializer> in the DCSwithDCR project.</span></span>

```csharp
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

#### <a name="to-use-this-sample"></a><span data-ttu-id="6fa5b-114">Aby użyć tego przykładu</span><span class="sxs-lookup"><span data-stu-id="6fa5b-114">To use this sample</span></span>

1. <span data-ttu-id="6fa5b-115">Za pomocą programu Visual Studio 2012 Otwórz plik rozwiązania DCRSample. sln.</span><span class="sxs-lookup"><span data-stu-id="6fa5b-115">Using Visual Studio 2012, open the DCRSample.sln solution file.</span></span>

2. <span data-ttu-id="6fa5b-116">Kliknij prawym przyciskiem myszy plik rozwiązania i wybierz polecenie **Właściwości**.</span><span class="sxs-lookup"><span data-stu-id="6fa5b-116">Right-click the solution file and choose **Properties**.</span></span>

3. <span data-ttu-id="6fa5b-117">W oknie dialogowym **strony właściwości rozwiązania** w obszarze **wspólne właściwości**, **projekt startowy**wybierz **wiele projektów startowych:** .</span><span class="sxs-lookup"><span data-stu-id="6fa5b-117">In the **Solution Property Pages** dialog, under **Common Properties**, **Startup Project**, select **Multiple startup projects:**.</span></span>

4. <span data-ttu-id="6fa5b-118">Obok projektu **DCSwithDCR** wybierz pozycję **Rozpocznij** z listy rozwijanej **Akcja** .</span><span class="sxs-lookup"><span data-stu-id="6fa5b-118">Next to the **DCSwithDCR** project, select **Start** from the **Action** dropdown.</span></span>

5. <span data-ttu-id="6fa5b-119">Obok projektu **NetDCS** wybierz pozycję **Rozpocznij** z listy rozwijanej **Akcja** .</span><span class="sxs-lookup"><span data-stu-id="6fa5b-119">Next to the **NetDCS** project, select **Start** from the **Action** dropdown.</span></span>

6. <span data-ttu-id="6fa5b-120">Kliknij przycisk **OK** , aby zamknąć okno dialogowe.</span><span class="sxs-lookup"><span data-stu-id="6fa5b-120">Click **OK** to close the dialog.</span></span>

7. <span data-ttu-id="6fa5b-121">Aby skompilować rozwiązanie, naciśnij klawisze CTRL + SHIFT + B.</span><span class="sxs-lookup"><span data-stu-id="6fa5b-121">To build the solution, press CTRL+SHIFT+B.</span></span>

8. <span data-ttu-id="6fa5b-122">Aby uruchomić rozwiązanie, naciśnij klawisze CTRL + F5.</span><span class="sxs-lookup"><span data-stu-id="6fa5b-122">To run the solution, press CTRL+F5.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="6fa5b-123">Przykłady mogą być już zainstalowane na komputerze.</span><span class="sxs-lookup"><span data-stu-id="6fa5b-123">The samples may already be installed on your machine.</span></span> <span data-ttu-id="6fa5b-124">Przed kontynuowaniem Wyszukaj następujący katalog (domyślny).</span><span class="sxs-lookup"><span data-stu-id="6fa5b-124">Check for the following (default) directory before continuing.</span></span>  
>   
> `<InstallDrive>:\WF_WCF_Samples`  
>   
> <span data-ttu-id="6fa5b-125">Jeśli ten katalog nie istnieje, przejdź do [przykładów Windows Communication Foundation (WCF) i Windows Workflow Foundation (WF) dla .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) , aby pobrać wszystkie Windows Communication Foundation (WCF) i [!INCLUDE[wf1](../../../../includes/wf1-md.md)] przykłady.</span><span class="sxs-lookup"><span data-stu-id="6fa5b-125">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="6fa5b-126">Ten przykład znajduje się w następującym katalogu.</span><span class="sxs-lookup"><span data-stu-id="6fa5b-126">This sample is located in the following directory.</span></span>  
>   
> `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Contract\Data\NetDcSasDcSwithDCR`  

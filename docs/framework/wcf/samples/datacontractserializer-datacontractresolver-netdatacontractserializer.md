---
title: Używanie elementów DataContractSerializer i DataContractResolver do udostępniania funkcji elementu NetDataContractSerializer
ms.date: 03/30/2017
ms.assetid: 1376658f-f695-45f7-a7e0-94664e9619ff
ms.openlocfilehash: e7a4f0d754b444d8558b03e07d98788a2eee5971
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/12/2020
ms.locfileid: "79144985"
---
# <a name="using-datacontractserializer-and-datacontractresolver-to-provide-the-functionality-of-netdatacontractserializer"></a><span data-ttu-id="5ef6b-102">Używanie elementów DataContractSerializer i DataContractResolver do udostępniania funkcji elementu NetDataContractSerializer</span><span class="sxs-lookup"><span data-stu-id="5ef6b-102">Using DataContractSerializer and DataContractResolver to Provide the Functionality of NetDataContractSerializer</span></span>
<span data-ttu-id="5ef6b-103">W tym przykładzie pokazano, w jaki sposób <xref:System.Runtime.Serialization.DataContractSerializer> użycie za pomocą odpowiedniego <xref:System.Runtime.Serialization.DataContractResolver> zapewnia taką samą funkcjonalność jak <xref:System.Runtime.Serialization.NetDataContractSerializer>.</span><span class="sxs-lookup"><span data-stu-id="5ef6b-103">This sample demonstrates how the use of <xref:System.Runtime.Serialization.DataContractSerializer> with an appropriate <xref:System.Runtime.Serialization.DataContractResolver> provides the same functionality as <xref:System.Runtime.Serialization.NetDataContractSerializer>.</span></span> <span data-ttu-id="5ef6b-104">W tym przykładzie pokazano, jak utworzyć <xref:System.Runtime.Serialization.DataContractResolver> odpowiednie <xref:System.Runtime.Serialization.DataContractSerializer>i jak dodać go do .</span><span class="sxs-lookup"><span data-stu-id="5ef6b-104">This sample shows how to create the appropriate <xref:System.Runtime.Serialization.DataContractResolver> and how to add it to the <xref:System.Runtime.Serialization.DataContractSerializer>.</span></span>

## <a name="sample-details"></a><span data-ttu-id="5ef6b-105">Przykładowe szczegóły</span><span class="sxs-lookup"><span data-stu-id="5ef6b-105">Sample details</span></span>
 <span data-ttu-id="5ef6b-106"><xref:System.Runtime.Serialization.NetDataContractSerializer>różni się <xref:System.Runtime.Serialization.DataContractSerializer> od w <xref:System.Runtime.Serialization.NetDataContractSerializer> jeden ważny sposób: zawiera informacje o typie CLR w serializowanym XML, podczas gdy <xref:System.Runtime.Serialization.DataContractSerializer> nie.</span><span class="sxs-lookup"><span data-stu-id="5ef6b-106"><xref:System.Runtime.Serialization.NetDataContractSerializer> differs from <xref:System.Runtime.Serialization.DataContractSerializer> in one important way: <xref:System.Runtime.Serialization.NetDataContractSerializer> includes CLR type information in the serialized XML, whereas <xref:System.Runtime.Serialization.DataContractSerializer> does not.</span></span> <span data-ttu-id="5ef6b-107">W związku <xref:System.Runtime.Serialization.NetDataContractSerializer> z tym może służyć tylko wtedy, gdy zarówno serializacji i deserializacji kończy współużytkować te same typy CLR.</span><span class="sxs-lookup"><span data-stu-id="5ef6b-107">Therefore, <xref:System.Runtime.Serialization.NetDataContractSerializer> can be used only if both the serializing and deserializing ends share the same CLR types.</span></span> <span data-ttu-id="5ef6b-108">Jednak zaleca się stosowanie, <xref:System.Runtime.Serialization.DataContractSerializer> ponieważ jego <xref:System.Runtime.Serialization.NetDataContractSerializer>wydajność jest lepsza niż .</span><span class="sxs-lookup"><span data-stu-id="5ef6b-108">However, it is recommended to use <xref:System.Runtime.Serialization.DataContractSerializer> because its performance is better than <xref:System.Runtime.Serialization.NetDataContractSerializer>.</span></span> <span data-ttu-id="5ef6b-109">Można zmienić informacje, które <xref:System.Runtime.Serialization.DataContractSerializer> są serializowane, dodając <xref:System.Runtime.Serialization.DataContractResolver> do niego.</span><span class="sxs-lookup"><span data-stu-id="5ef6b-109">You can change the information that is serialized in <xref:System.Runtime.Serialization.DataContractSerializer> by adding a <xref:System.Runtime.Serialization.DataContractResolver> to it.</span></span>

 <span data-ttu-id="5ef6b-110">Ten przykład składa się z dwóch projektów.</span><span class="sxs-lookup"><span data-stu-id="5ef6b-110">This sample consists of two projects.</span></span> <span data-ttu-id="5ef6b-111">Pierwszy projekt używa <xref:System.Runtime.Serialization.NetDataContractSerializer> do serializacji obiektu.</span><span class="sxs-lookup"><span data-stu-id="5ef6b-111">The first project uses <xref:System.Runtime.Serialization.NetDataContractSerializer> to serialize an object.</span></span> <span data-ttu-id="5ef6b-112">Drugi projekt używa <xref:System.Runtime.Serialization.DataContractSerializer> z <xref:System.Runtime.Serialization.DataContractResolver> a, aby zapewnić taką samą funkcjonalność jak pierwszy projekt.</span><span class="sxs-lookup"><span data-stu-id="5ef6b-112">The second project uses <xref:System.Runtime.Serialization.DataContractSerializer> with a <xref:System.Runtime.Serialization.DataContractResolver> to provide the same functionality as the first project.</span></span>

 <span data-ttu-id="5ef6b-113">Poniższy przykład kodu pokazuje implementację niestandardowej <xref:System.Runtime.Serialization.DataContractResolver> nazwie, `MyDataContractResolver` która jest dodawana <xref:System.Runtime.Serialization.DataContractSerializer> do projektu DCSwithDCR.</span><span class="sxs-lookup"><span data-stu-id="5ef6b-113">The following code example shows the implementation of a custom <xref:System.Runtime.Serialization.DataContractResolver> named `MyDataContractResolver` that is added to the <xref:System.Runtime.Serialization.DataContractSerializer> in the DCSwithDCR project.</span></span>

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
        type ??= Type.GetType(typeName + ", " + typeNamespace);
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

#### <a name="to-use-this-sample"></a><span data-ttu-id="5ef6b-114">Aby użyć tej próbki</span><span class="sxs-lookup"><span data-stu-id="5ef6b-114">To use this sample</span></span>

1. <span data-ttu-id="5ef6b-115">Za pomocą programu Visual Studio 2012 otwórz plik rozwiązania DCRSample.sln.</span><span class="sxs-lookup"><span data-stu-id="5ef6b-115">Using Visual Studio 2012, open the DCRSample.sln solution file.</span></span>

2. <span data-ttu-id="5ef6b-116">Kliknij prawym przyciskiem myszy plik rozwiązania i wybierz polecenie **Właściwości**.</span><span class="sxs-lookup"><span data-stu-id="5ef6b-116">Right-click the solution file and choose **Properties**.</span></span>

3. <span data-ttu-id="5ef6b-117">W oknie dialogowym **Strony właściwości rozwiązania** w obszarze Wspólne **właściwości**, **Projekt uruchamiania**wybierz pozycję **Wiele projektów startowych:**.</span><span class="sxs-lookup"><span data-stu-id="5ef6b-117">In the **Solution Property Pages** dialog, under **Common Properties**, **Startup Project**, select **Multiple startup projects:**.</span></span>

4. <span data-ttu-id="5ef6b-118">Obok projektu **DCSwithDCR** wybierz pozycję **Start** z listy rozwijanej **Akcja.**</span><span class="sxs-lookup"><span data-stu-id="5ef6b-118">Next to the **DCSwithDCR** project, select **Start** from the **Action** dropdown.</span></span>

5. <span data-ttu-id="5ef6b-119">Obok projektu **NetDCS** wybierz pozycję **Start** z listy rozwijanej **Akcja.**</span><span class="sxs-lookup"><span data-stu-id="5ef6b-119">Next to the **NetDCS** project, select **Start** from the **Action** dropdown.</span></span>

6. <span data-ttu-id="5ef6b-120">Kliknij **przycisk OK,** aby zamknąć okno dialogowe.</span><span class="sxs-lookup"><span data-stu-id="5ef6b-120">Click **OK** to close the dialog.</span></span>

7. <span data-ttu-id="5ef6b-121">Aby utworzyć rozwiązanie, naciśnij klawisze CTRL+SHIFT+B.</span><span class="sxs-lookup"><span data-stu-id="5ef6b-121">To build the solution, press CTRL+SHIFT+B.</span></span>

8. <span data-ttu-id="5ef6b-122">Aby uruchomić rozwiązanie, naciśnij klawisze CTRL+F5.</span><span class="sxs-lookup"><span data-stu-id="5ef6b-122">To run the solution, press CTRL+F5.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="5ef6b-123">Próbki mogą być już zainstalowane na komputerze.</span><span class="sxs-lookup"><span data-stu-id="5ef6b-123">The samples may already be installed on your machine.</span></span> <span data-ttu-id="5ef6b-124">Przed kontynuowaniem sprawdź następujący (domyślny) katalog.</span><span class="sxs-lookup"><span data-stu-id="5ef6b-124">Check for the following (default) directory before continuing.</span></span>  
>
> `<InstallDrive>:\WF_WCF_Samples`  
>
> <span data-ttu-id="5ef6b-125">Jeśli ten katalog nie istnieje, przejdź do [Windows Communication Foundation (WCF) i Windows Workflow Foundation (WF) Przykłady dla platformy .NET Framework 4,](https://www.microsoft.com/download/details.aspx?id=21459) aby pobrać wszystkie Windows Communication Foundation (WCF) i [!INCLUDE[wf1](../../../../includes/wf1-md.md)] przykłady.</span><span class="sxs-lookup"><span data-stu-id="5ef6b-125">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="5ef6b-126">Ten przykład znajduje się w następującym katalogu.</span><span class="sxs-lookup"><span data-stu-id="5ef6b-126">This sample is located in the following directory.</span></span>  
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Contract\Data\NetDcSasDcSwithDCR`  

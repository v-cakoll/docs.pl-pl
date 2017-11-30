---
title: "Użycie działanie Switch z niestandardowych typów"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 482a48c4-eb83-40c3-a4e2-2f9a8af88b75
caps.latest.revision: "10"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 57a6a15f648f83a60f3ac402443c3c5e4aecfcd4
ms.sourcegitcommit: 5177d6ae2e9baf026f07ee0631556700a5a193f7
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/28/2017
---
# <a name="usage-of-the-switch-activity-with-custom-types"></a><span data-ttu-id="cb68e-102">Użycie działanie Switch z niestandardowych typów</span><span class="sxs-lookup"><span data-stu-id="cb68e-102">Usage of the Switch Activity with Custom Types</span></span>
<span data-ttu-id="cb68e-103">W tym przykładzie opisano, jak włączyć <xref:System.Activities.Statements.Switch%601> działanie, aby ocenić typu złożonego zdefiniowane przez użytkownika w czasie wykonywania.</span><span class="sxs-lookup"><span data-stu-id="cb68e-103">This sample describes how to enable a <xref:System.Activities.Statements.Switch%601> activity to evaluate a user-defined complex type at runtime.</span></span> <span data-ttu-id="cb68e-104">W procedurach najbardziej tradycyjnych językach programowania [przełącznika](http://go.microsoft.com/fwlink/?LinkId=180521) instrukcja wybiera logiki wykonywania oparte na ocenie warunkowy zmiennej.</span><span class="sxs-lookup"><span data-stu-id="cb68e-104">In most traditional procedural programming languages, a [switch](http://go.microsoft.com/fwlink/?LinkId=180521) statement selects an execution logic based on the conditional evaluation of a variable.</span></span> <span data-ttu-id="cb68e-105">Tradycyjnie `switch` instrukcji działa na wyrażenie, które może przyjąć statycznie.</span><span class="sxs-lookup"><span data-stu-id="cb68e-105">Traditionally, a `switch` statement operates on an expression that can be statically evaluated.</span></span> <span data-ttu-id="cb68e-106">Na przykład w języku C# to oznacza, że typy tego tylko pierwotne, takie jak <xref:System.Boolean>, <xref:System.Int32>, <xref:System.String>, i typy wyliczeniowe są obsługiwane.</span><span class="sxs-lookup"><span data-stu-id="cb68e-106">For example, in C# this means that only primitive types, such as <xref:System.Boolean>, <xref:System.Int32>, <xref:System.String>, and enumeration types are supported.</span></span>  
  
 <span data-ttu-id="cb68e-107">Umożliwia włączenie klasy niestandardowej logiki musi być implementowana pozwala obliczyć wartości typu złożonego niestandardowych w czasie wykonywania.</span><span class="sxs-lookup"><span data-stu-id="cb68e-107">To enable switching on a custom class, logic must be implemented to evaluate values of the custom complex type at runtime.</span></span> <span data-ttu-id="cb68e-108">W tym przykładzie pokazano, jak włączyć włączenie niestandardowego typu złożonego o nazwie `Person`.</span><span class="sxs-lookup"><span data-stu-id="cb68e-108">This sample demonstrates how to enable switching on a custom complex type named `Person`.</span></span>  
  
-   <span data-ttu-id="cb68e-109">W niestandardowej klasy `Person`, <xref:System.ComponentModel.TypeConverter> zadeklarowano atrybutu o nazwie niestandardowego <xref:System.ComponentModel.TypeConverter>.</span><span class="sxs-lookup"><span data-stu-id="cb68e-109">In the custom class `Person`, a <xref:System.ComponentModel.TypeConverter> attribute is declared with the name of the custom <xref:System.ComponentModel.TypeConverter>.</span></span>  
  
    ```  
    [TypeConverter(typeof(PersonConverter))]  
    public class Person  
    {  
       public string Name { get; set; }  
       public int Age { get; set; }  
    ...  
    ```  
  
-   <span data-ttu-id="cb68e-110">W niestandardowej klasy `Person`, <xref:System.Object.Equals%2A> i <xref:System.Object.GetHashCode%2A> klasy zostaną zastąpione.</span><span class="sxs-lookup"><span data-stu-id="cb68e-110">In the custom class `Person`, the <xref:System.Object.Equals%2A> and <xref:System.Object.GetHashCode%2A> classes are overridden.</span></span>  
  
    ```  
    public override bool Equals(object obj)  
    {  
        Person person = obj as Person;  
  
        if (person != null)  
        {  
            return string.Equals(this.Name, person.Name);  
        }  
  
        return false;  
    }  
  
    public override int GetHashCode()  
    {  
        if (this.Name != null)  
        {  
            return this.Name.GetHashCode();  
        }  
  
        return 0;  
    }  
    ```  
  
-   <span data-ttu-id="cb68e-111">Niestandardowy <xref:System.ComponentModel.TypeConverter> zaimplementowana jest klasa, która przeprowadza konwersję wystąpienia klasy niestandardowego ciągu i ciąg do wystąpienia klasy niestandardowej.</span><span class="sxs-lookup"><span data-stu-id="cb68e-111">A custom <xref:System.ComponentModel.TypeConverter> class is implemented that performs the conversion of an instance of the custom class to a string and a string to an instance of a custom class.</span></span>  
  
    ```  
    public class PersonConverter : TypeConverter  
    {  
        public override bool CanConvertFrom(ITypeDescriptorContext context,  
           Type sourceType)  
        {  
            return (sourceType is string);  
        }  
  
        // Overrides the ConvertFrom method of TypeConverter.  
        public override object ConvertFrom(ITypeDescriptorContext context,  
           CultureInfo culture, object value)  
        {  
            if (value == null)  
            {  
                return null;  
            }  
  
            if (value is string)  
            {  
                return new Person  
                {  
                    Name = (string)value  
                };  
            }  
  
            return base.ConvertFrom(context, culture, value);  
        }  
  
        // Overrides the ConvertTo method of TypeConverter.  
        public override object ConvertTo(ITypeDescriptorContext context,  
           CultureInfo culture, object value, Type destinationType)  
        {  
            if (destinationType == typeof(string))  
            {  
                if (value != null)  
                {  
                    return ((Person) value).Name;  
                }  
                else  
                {  
                    return null;  
                }  
            }  
  
            return base.ConvertTo(context, culture, value, destinationType);  
        }  
    }  
    ```  
  
 <span data-ttu-id="cb68e-112">Następujące pliki znajdują się w tym przykładzie:</span><span class="sxs-lookup"><span data-stu-id="cb68e-112">The following files are included in this sample:</span></span>  
  
-   <span data-ttu-id="cb68e-113">**Person.cs**: definiuje `Person` klasy.</span><span class="sxs-lookup"><span data-stu-id="cb68e-113">**Person.cs**: Defines the `Person` class.</span></span>  
  
-   <span data-ttu-id="cb68e-114">**PersonConverter.cs**: konwerter typów dla `Person` klasy.</span><span class="sxs-lookup"><span data-stu-id="cb68e-114">**PersonConverter.cs**: The type converter for the `Person` class.</span></span>  
  
-   <span data-ttu-id="cb68e-115">**Sequence.XAML**: przepływ pracy, który przełącza `Person` typu.</span><span class="sxs-lookup"><span data-stu-id="cb68e-115">**Sequence.xaml**: a workflow that switches over the `Person` type.</span></span>  
  
-   <span data-ttu-id="cb68e-116">**Plik program.cs**: funkcja main, która uruchamia przepływ pracy.</span><span class="sxs-lookup"><span data-stu-id="cb68e-116">**Program.cs**: The main function that runs the workflow.</span></span>  
  
#### <a name="to-use-this-sample"></a><span data-ttu-id="cb68e-117">Aby użyć tego przykładu</span><span class="sxs-lookup"><span data-stu-id="cb68e-117">To use this sample</span></span>  
  
1.  <span data-ttu-id="cb68e-118">Ładowanie Switch.sln w [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)].</span><span class="sxs-lookup"><span data-stu-id="cb68e-118">Load Switch.sln in [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)].</span></span>  
  
2.  <span data-ttu-id="cb68e-119">Naciśnij klawisze CTRL + SHIFT + B w celu skompilowania rozwiązania.</span><span class="sxs-lookup"><span data-stu-id="cb68e-119">Press CTRL+SHIFT+B to build the solution.</span></span>  
  
3.  <span data-ttu-id="cb68e-120">Naciśnij klawisze CTRL + F5, aby uruchomić przykład.</span><span class="sxs-lookup"><span data-stu-id="cb68e-120">Press CTRL + F5 to run the sample.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="cb68e-121">Próbki mogą być zainstalowane na tym komputerze.</span><span class="sxs-lookup"><span data-stu-id="cb68e-121">The samples may already be installed on your machine.</span></span> <span data-ttu-id="cb68e-122">Przed kontynuowaniem sprawdź, czy są dostępne dla następującego katalogu (ustawienie domyślne).</span><span class="sxs-lookup"><span data-stu-id="cb68e-122">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="cb68e-123">Jeśli ten katalog nie istnieje, przejdź do [Windows Communication Foundation (WCF) i Windows Workflow Foundation (WF) przykłady dla programu .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) pobrać wszystkie [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] i [!INCLUDE[wf1](../../../../includes/wf1-md.md)] próbek.</span><span class="sxs-lookup"><span data-stu-id="cb68e-123">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) to download all [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="cb68e-124">W tym przykładzie znajduje się w następującym katalogu.</span><span class="sxs-lookup"><span data-stu-id="cb68e-124">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Basic\Built-InActivities\Switch`  
  
## <a name="see-also"></a><span data-ttu-id="cb68e-125">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="cb68e-125">See Also</span></span>  
 [<span data-ttu-id="cb68e-126">Biblioteka działań wbudowanych</span><span class="sxs-lookup"><span data-stu-id="cb68e-126">Built-In Activity Library</span></span>](../../../../docs/framework/windows-workflow-foundation/net-framework-4-5-built-in-activity-library.md)

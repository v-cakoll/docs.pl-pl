---
title: 'Instrukcje: Klonowanie drukarki'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- print queues [WPF]
- cloning printers [WPF]
- printers [WPF], cloning
- print queues [WPF], cloning
- cloning print queues [WPF]
ms.assetid: dd6997c9-fe04-40f8-88a6-92e3ac0889eb
ms.openlocfilehash: 09a445da068f0141b9526e0228df8be0105498c6
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/18/2019
ms.locfileid: "59310463"
---
# <a name="how-to-clone-a-printer"></a><span data-ttu-id="664d6-102">Instrukcje: Klonowanie drukarki</span><span class="sxs-lookup"><span data-stu-id="664d6-102">How to: Clone a Printer</span></span>
<span data-ttu-id="664d6-103">Większość firm w pewnym momencie kupić wiele drukarek tego samego modelu.</span><span class="sxs-lookup"><span data-stu-id="664d6-103">Most businesses will, at some point, buy multiple printers of the same model.</span></span> <span data-ttu-id="664d6-104">Zazwyczaj te wszystkie są instalowane przy użyciu ustawień konfiguracyjnych niemal identyczne.</span><span class="sxs-lookup"><span data-stu-id="664d6-104">Typically, these are all installed with virtually identical configuration settings.</span></span> <span data-ttu-id="664d6-105">Instalowanie poszczególnych drukarki może być czasochłonne i podatne.</span><span class="sxs-lookup"><span data-stu-id="664d6-105">Installing each printer can be time-consuming and error prone.</span></span> <span data-ttu-id="664d6-106"><xref:System.Printing.IndexedProperties?displayProperty=nameWithType> Przestrzeni nazw i <xref:System.Printing.PrintServer.InstallPrintQueue%2A> klasy, które są udostępniane za pomocą programu Microsoft .NET Framework umożliwia natychmiastowe zainstalować dowolną liczbę dodatkowych kolejek drukowania, które są klonowane z istniejącej kolejki wydruku.</span><span class="sxs-lookup"><span data-stu-id="664d6-106">The <xref:System.Printing.IndexedProperties?displayProperty=nameWithType> namespace and the <xref:System.Printing.PrintServer.InstallPrintQueue%2A> class that are exposed with Microsoft .NET Framework makes it possible to instantly install any number of additional print queues that are cloned from an existing print queue.</span></span>  
  
## <a name="example"></a><span data-ttu-id="664d6-107">Przykład</span><span class="sxs-lookup"><span data-stu-id="664d6-107">Example</span></span>  
 <span data-ttu-id="664d6-108">W poniższym przykładzie druga kolejki wydruku został sklonowany z istniejącej kolejki wydruku.</span><span class="sxs-lookup"><span data-stu-id="664d6-108">In the example below, a second print queue is cloned from an existing print queue.</span></span> <span data-ttu-id="664d6-109">Drugi różni się od pierwszego tylko w przypadku nazwy, lokalizacji, port i udostępniony stan.</span><span class="sxs-lookup"><span data-stu-id="664d6-109">The second differs from the first only in its name, location, port, and shared status.</span></span> <span data-ttu-id="664d6-110">Oto główne kroki w ten sposób.</span><span class="sxs-lookup"><span data-stu-id="664d6-110">The major steps for doing this are as follows.</span></span>  
  
1. <span data-ttu-id="664d6-111">Utwórz <xref:System.Printing.PrintQueue> obiektu dla istniejącej drukarki, która ma być klonowane.</span><span class="sxs-lookup"><span data-stu-id="664d6-111">Create a <xref:System.Printing.PrintQueue> object for the existing printer that is going to be cloned.</span></span>  
  
2. <span data-ttu-id="664d6-112">Tworzenie <xref:System.Printing.IndexedProperties.PrintPropertyDictionary> z <xref:System.Printing.PrintSystemObject.PropertiesCollection%2A> z <xref:System.Printing.PrintQueue>.</span><span class="sxs-lookup"><span data-stu-id="664d6-112">Create a <xref:System.Printing.IndexedProperties.PrintPropertyDictionary> from the <xref:System.Printing.PrintSystemObject.PropertiesCollection%2A> of the <xref:System.Printing.PrintQueue>.</span></span> <span data-ttu-id="664d6-113"><xref:System.Collections.DictionaryEntry.Value%2A> Właściwości każdego wpisu, w tym słowniku jest obiektem, jednego z typów pochodnych typu <xref:System.Printing.IndexedProperties.PrintProperty>.</span><span class="sxs-lookup"><span data-stu-id="664d6-113">The <xref:System.Collections.DictionaryEntry.Value%2A> property of each entry in this dictionary is an object of one of the types derived from <xref:System.Printing.IndexedProperties.PrintProperty>.</span></span> <span data-ttu-id="664d6-114">Istnieją dwa sposoby, aby ustawić wartość wpisu w tym słowniku.</span><span class="sxs-lookup"><span data-stu-id="664d6-114">There are two ways to set the value of an entry in this dictionary.</span></span>  
  
    -   <span data-ttu-id="664d6-115">Użyj słownika **Usuń** i <xref:System.Printing.IndexedProperties.PrintPropertyDictionary.Add%2A> metody Usuń wpis, a następnie dodaj go ponownie z wymaganą wartość.</span><span class="sxs-lookup"><span data-stu-id="664d6-115">Use the dictionary's **Remove** and <xref:System.Printing.IndexedProperties.PrintPropertyDictionary.Add%2A> methods to remove the entry and then re-add it with the desired value.</span></span>  
  
    -   <span data-ttu-id="664d6-116">Użyj słownika <xref:System.Printing.IndexedProperties.PrintPropertyDictionary.SetProperty%2A> metody.</span><span class="sxs-lookup"><span data-stu-id="664d6-116">Use the dictionary's <xref:System.Printing.IndexedProperties.PrintPropertyDictionary.SetProperty%2A> method.</span></span>  
  
     <span data-ttu-id="664d6-117">W poniższym przykładzie przedstawiono w obu kierunkach.</span><span class="sxs-lookup"><span data-stu-id="664d6-117">The example below illustrates both ways.</span></span>  
  
3. <span data-ttu-id="664d6-118">Tworzenie <xref:System.Printing.IndexedProperties.PrintBooleanProperty> obiektu i ustaw jego <xref:System.Printing.IndexedProperties.PrintProperty.Name%2A> do "IsShared" i jego <xref:System.Printing.IndexedProperties.PrintBooleanProperty.Value%2A> do `true`.</span><span class="sxs-lookup"><span data-stu-id="664d6-118">Create a <xref:System.Printing.IndexedProperties.PrintBooleanProperty> object and set its <xref:System.Printing.IndexedProperties.PrintProperty.Name%2A> to "IsShared" and its <xref:System.Printing.IndexedProperties.PrintBooleanProperty.Value%2A> to `true`.</span></span>  
  
4. <span data-ttu-id="664d6-119">Użyj <xref:System.Printing.IndexedProperties.PrintBooleanProperty> obiektu jako wartość <xref:System.Printing.IndexedProperties.PrintPropertyDictionary>firmy wpis "IsShared".</span><span class="sxs-lookup"><span data-stu-id="664d6-119">Use the <xref:System.Printing.IndexedProperties.PrintBooleanProperty> object to be the value of the <xref:System.Printing.IndexedProperties.PrintPropertyDictionary>'s "IsShared" entry.</span></span>  
  
5. <span data-ttu-id="664d6-120">Tworzenie <xref:System.Printing.IndexedProperties.PrintStringProperty> obiektu i ustaw jego <xref:System.Printing.IndexedProperties.PrintProperty.Name%2A> do "Nazwa_udziału" i jego <xref:System.Printing.IndexedProperties.PrintStringProperty.Value%2A> do odpowiedniej <xref:System.String>.</span><span class="sxs-lookup"><span data-stu-id="664d6-120">Create a <xref:System.Printing.IndexedProperties.PrintStringProperty> object and set its <xref:System.Printing.IndexedProperties.PrintProperty.Name%2A> to "ShareName" and its <xref:System.Printing.IndexedProperties.PrintStringProperty.Value%2A> to an appropriate <xref:System.String>.</span></span>  
  
6. <span data-ttu-id="664d6-121">Użyj <xref:System.Printing.IndexedProperties.PrintStringProperty> obiektu jako wartość <xref:System.Printing.IndexedProperties.PrintPropertyDictionary>firmy wpis "Nazwa_udziału".</span><span class="sxs-lookup"><span data-stu-id="664d6-121">Use the <xref:System.Printing.IndexedProperties.PrintStringProperty> object to be the value of the <xref:System.Printing.IndexedProperties.PrintPropertyDictionary>'s "ShareName" entry.</span></span>  
  
7. <span data-ttu-id="664d6-122">Utworzyć kolejną <xref:System.Printing.IndexedProperties.PrintStringProperty> obiektu i ustaw jego <xref:System.Printing.IndexedProperties.PrintProperty.Name%2A> do "Lokalizacja" i jego <xref:System.Printing.IndexedProperties.PrintStringProperty.Value%2A> do odpowiedniej <xref:System.String>.</span><span class="sxs-lookup"><span data-stu-id="664d6-122">Create another <xref:System.Printing.IndexedProperties.PrintStringProperty> object and set its <xref:System.Printing.IndexedProperties.PrintProperty.Name%2A> to "Location" and its <xref:System.Printing.IndexedProperties.PrintStringProperty.Value%2A> to an appropriate <xref:System.String>.</span></span>  
  
8. <span data-ttu-id="664d6-123">Drugą <xref:System.Printing.IndexedProperties.PrintStringProperty> obiektu jako wartość <xref:System.Printing.IndexedProperties.PrintPropertyDictionary>firmy wpis "Lokalizacja".</span><span class="sxs-lookup"><span data-stu-id="664d6-123">Use the second <xref:System.Printing.IndexedProperties.PrintStringProperty> object to be the value of the <xref:System.Printing.IndexedProperties.PrintPropertyDictionary>'s "Location" entry.</span></span>  
  
9. <span data-ttu-id="664d6-124">Utwórz tablicę <xref:System.String>s.</span><span class="sxs-lookup"><span data-stu-id="664d6-124">Create an array of <xref:System.String>s.</span></span> <span data-ttu-id="664d6-125">Każdy element jest nazwa portu na serwerze.</span><span class="sxs-lookup"><span data-stu-id="664d6-125">Each item is the name of a port on the server.</span></span>  
  
10. <span data-ttu-id="664d6-126">Użyj <xref:System.Printing.PrintServer.InstallPrintQueue%2A> do zainstalowania nowej drukarki z nowymi wartościami.</span><span class="sxs-lookup"><span data-stu-id="664d6-126">Use <xref:System.Printing.PrintServer.InstallPrintQueue%2A> to install the new printer with the new values.</span></span>  
  
 <span data-ttu-id="664d6-127">Przykład znajduje się poniżej.</span><span class="sxs-lookup"><span data-stu-id="664d6-127">An example is below.</span></span>  
  
 [!code-csharp[ClonePrinter#ClonePrinter](~/samples/snippets/csharp/VS_Snippets_Wpf/ClonePrinter/CSharp/Program.cs#cloneprinter)]
 [!code-vb[ClonePrinter#ClonePrinter](~/samples/snippets/visualbasic/VS_Snippets_Wpf/ClonePrinter/visualbasic/program.vb#cloneprinter)]  
  
## <a name="see-also"></a><span data-ttu-id="664d6-128">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="664d6-128">See also</span></span>

- <xref:System.Printing.IndexedProperties>
- <xref:System.Printing.IndexedProperties.PrintPropertyDictionary>
- <xref:System.Printing.LocalPrintServer>
- <xref:System.Printing.PrintQueue>
- <xref:System.Collections.DictionaryEntry>
- [<span data-ttu-id="664d6-129">Dokumenty w WPF</span><span class="sxs-lookup"><span data-stu-id="664d6-129">Documents in WPF</span></span>](documents-in-wpf.md)
- [<span data-ttu-id="664d6-130">Przegląd drukowania</span><span class="sxs-lookup"><span data-stu-id="664d6-130">Printing Overview</span></span>](printing-overview.md)

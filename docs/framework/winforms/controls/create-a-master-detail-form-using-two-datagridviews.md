---
title: Tworzenie formularza z szczegółami głównymi przy użyciu dwóch formantów DataGridView
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- DataGridView control [Windows Forms], master/detail form
- parent-child tables [Windows Forms], displaying on Windows Forms
- master-details lists [Windows Forms], creating
ms.assetid: 99f6e876-3f7f-4139-9063-e36587c95b02
ms.openlocfilehash: d317f4e592790c9b48b539b1601814569e14529f
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/24/2020
ms.locfileid: "76737333"
---
# <a name="how-to-create-a-masterdetail-form-using-two-windows-forms-datagridview-controls"></a><span data-ttu-id="57da5-102">Porady: tworzenie formularza wzorzec/szczegół za pomocą dwóch formantów DataGridView formularzy systemu Windows</span><span class="sxs-lookup"><span data-stu-id="57da5-102">How to: Create a Master/Detail Form Using Two Windows Forms DataGridView Controls</span></span>
<span data-ttu-id="57da5-103">Poniższy przykład kodu tworzy formularz wzorzec/szczegół za pomocą dwóch formantów <xref:System.Windows.Forms.DataGridView> powiązanych z dwoma składnikami <xref:System.Windows.Forms.BindingSource>.</span><span class="sxs-lookup"><span data-stu-id="57da5-103">The following code example creates a master/detail form using two <xref:System.Windows.Forms.DataGridView> controls bound to two <xref:System.Windows.Forms.BindingSource> components.</span></span> <span data-ttu-id="57da5-104">Źródło danych to <xref:System.Data.DataSet>, które zawiera tabele `Customers` i `Orders` z przykładowej bazy danych Northwind SQL Server wraz z <xref:System.Data.DataRelation>, który wiąże te dwa za pośrednictwem kolumny `CustomerID`.</span><span class="sxs-lookup"><span data-stu-id="57da5-104">The data source is a <xref:System.Data.DataSet> that contains the `Customers` and `Orders` tables from the Northwind SQL Server sample database along with a <xref:System.Data.DataRelation> that relates the two through the `CustomerID` column.</span></span>  
  
 <span data-ttu-id="57da5-105">Jeden <xref:System.Windows.Forms.BindingSource> jest powiązany z tabelą nadrzędną `Customers` w zestawie danych.</span><span class="sxs-lookup"><span data-stu-id="57da5-105">One <xref:System.Windows.Forms.BindingSource> is bound to the parent `Customers` table in the data set.</span></span> <span data-ttu-id="57da5-106">Te dane są wyświetlane w głównym formancie <xref:System.Windows.Forms.DataGridView>.</span><span class="sxs-lookup"><span data-stu-id="57da5-106">This data is displayed in the master <xref:System.Windows.Forms.DataGridView> control.</span></span> <span data-ttu-id="57da5-107">Inne <xref:System.Windows.Forms.BindingSource> są powiązane z pierwszym łącznikiem danych.</span><span class="sxs-lookup"><span data-stu-id="57da5-107">The other <xref:System.Windows.Forms.BindingSource> is bound to the first data connector.</span></span> <span data-ttu-id="57da5-108">Właściwość <xref:System.Windows.Forms.BindingSource.DataMember%2A> drugiego <xref:System.Windows.Forms.BindingSource> jest ustawiona na nazwę <xref:System.Data.DataRelation>.</span><span class="sxs-lookup"><span data-stu-id="57da5-108">The <xref:System.Windows.Forms.BindingSource.DataMember%2A> property of the second <xref:System.Windows.Forms.BindingSource> is set to the <xref:System.Data.DataRelation> name.</span></span> <span data-ttu-id="57da5-109">Powoduje to, że skojarzona szczegółowo formant <xref:System.Windows.Forms.DataGridView> formantu, aby wyświetlić wiersze podrzędnej tabeli `Orders`, która odpowiada bieżącemu wierszowi w głównym formancie <xref:System.Windows.Forms.DataGridView>.</span><span class="sxs-lookup"><span data-stu-id="57da5-109">This causes the associated detail <xref:System.Windows.Forms.DataGridView> control to display the rows of the child `Orders` table that correspond to the current row in the master <xref:System.Windows.Forms.DataGridView> control.</span></span>  
  
 <span data-ttu-id="57da5-110">Aby uzyskać kompletny opis tego przykładu kodu, zobacz [Przewodnik: Tworzenie formularza wzorzec/szczegół za pomocą dwóch Windows Forms formantów DataGridView](creating-a-master-detail-form-using-two-datagridviews.md).</span><span class="sxs-lookup"><span data-stu-id="57da5-110">For a complete explanation of this code example, see [Walkthrough: Creating a Master/Detail Form Using Two Windows Forms DataGridView Controls](creating-a-master-detail-form-using-two-datagridviews.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="57da5-111">Przykład</span><span class="sxs-lookup"><span data-stu-id="57da5-111">Example</span></span>  
 [!code-csharp[System.Windows.Forms.DataGridViewMasterDetails#00](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMasterDetails/CS/masterdetails.cs#00)]
 [!code-vb[System.Windows.Forms.DataGridViewMasterDetails#00](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMasterDetails/VB/masterdetails.vb#00)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="57da5-112">Kompilowanie kodu</span><span class="sxs-lookup"><span data-stu-id="57da5-112">Compiling the Code</span></span>  
 <span data-ttu-id="57da5-113">Ten przykład wymaga:</span><span class="sxs-lookup"><span data-stu-id="57da5-113">This example requires:</span></span>  
  
 <span data-ttu-id="57da5-114">Odwołania do zestawów system, system. Data, system. Windows. Forms i system. XML.</span><span class="sxs-lookup"><span data-stu-id="57da5-114">References to the System, System.Data, System.Windows.Forms, and System.XML assemblies.</span></span>  
  
## <a name="net-framework-security"></a><span data-ttu-id="57da5-115">Zabezpieczenia.NET Framework</span><span class="sxs-lookup"><span data-stu-id="57da5-115">.NET Framework Security</span></span>  
 <span data-ttu-id="57da5-116">Przechowywanie poufnych informacji, takich jak hasło, w ciągu połączenia może wpłynąć na bezpieczeństwo aplikacji.</span><span class="sxs-lookup"><span data-stu-id="57da5-116">Storing sensitive information, such as a password, within the connection string can affect the security of your application.</span></span> <span data-ttu-id="57da5-117">Korzystanie z uwierzytelniania systemu Windows (znanego również jako zabezpieczenia zintegrowane) jest bezpieczniejszym sposobem na kontrolowanie dostępu do bazy danych.</span><span class="sxs-lookup"><span data-stu-id="57da5-117">Using Windows Authentication (also known as integrated security) is a more secure way to control access to a database.</span></span> <span data-ttu-id="57da5-118">Aby uzyskać więcej informacji, zobacz [Ochrona informacji o połączeniu](../../data/adonet/protecting-connection-information.md).</span><span class="sxs-lookup"><span data-stu-id="57da5-118">For more information, see [Protecting Connection Information](../../data/adonet/protecting-connection-information.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="57da5-119">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="57da5-119">See also</span></span>

- <xref:System.Windows.Forms.DataGridView>
- <xref:System.Windows.Forms.BindingSource>
- [<span data-ttu-id="57da5-120">Przewodnik: tworzenie formularza wzorzec/szczegół za pomocą dwóch kontrolek DataGridView formularzy Windows Forms</span><span class="sxs-lookup"><span data-stu-id="57da5-120">Walkthrough: Creating a Master/Detail Form Using Two Windows Forms DataGridView Controls</span></span>](creating-a-master-detail-form-using-two-datagridviews.md)
- [<span data-ttu-id="57da5-121">Wyświetlanie danych w kontrolce DataGridView formularzy Windows Forms</span><span class="sxs-lookup"><span data-stu-id="57da5-121">Displaying Data in the Windows Forms DataGridView Control</span></span>](displaying-data-in-the-windows-forms-datagridview-control.md)
- [<span data-ttu-id="57da5-122">Ochrona informacji o połączeniu</span><span class="sxs-lookup"><span data-stu-id="57da5-122">Protecting Connection Information</span></span>](../../data/adonet/protecting-connection-information.md)

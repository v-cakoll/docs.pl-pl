---
title: 'Instrukcje: Określanie, które elementy członkowskie są sprawdzane pod kątem konfliktów współbieżności'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: d2cda293-1e2f-4878-af0e-5aaf0d092120
ms.openlocfilehash: fc6fafa474805c2644bb2deabdceed192776ac76
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2019
ms.locfileid: "69938751"
---
# <a name="how-to-specify-which-members-are-tested-for-concurrency-conflicts"></a><span data-ttu-id="8768b-102">Instrukcje: Określanie, które elementy członkowskie są sprawdzane pod kątem konfliktów współbieżności</span><span class="sxs-lookup"><span data-stu-id="8768b-102">How to: Specify Which Members are Tested for Concurrency Conflicts</span></span>
<span data-ttu-id="8768b-103">Zastosuj jeden z trzech typów wyliczeniowych [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] do <xref:System.Data.Linq.Mapping.ColumnAttribute.UpdateCheck%2A> właściwości <xref:System.Data.Linq.Mapping.ColumnAttribute> atrybutu, aby określić, które składowe mają być uwzględnione w testach aktualizacji w celu wykrywania optymistycznych konfliktów współbieżności.</span><span class="sxs-lookup"><span data-stu-id="8768b-103">Apply one of three enums to the [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] <xref:System.Data.Linq.Mapping.ColumnAttribute.UpdateCheck%2A> property on a <xref:System.Data.Linq.Mapping.ColumnAttribute> attribute to specify which members are to be included in update checks for the detection of optimistic concurrency conflicts.</span></span>  
  
 <span data-ttu-id="8768b-104">Właściwość (zamapowana w czasie projektowania) jest używana razem z funkcjami współbieżności w czasie wykonywania [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]w systemie. <xref:System.Data.Linq.Mapping.ColumnAttribute.UpdateCheck%2A></span><span class="sxs-lookup"><span data-stu-id="8768b-104">The <xref:System.Data.Linq.Mapping.ColumnAttribute.UpdateCheck%2A> property (mapped at design time) is used together with run-time concurrency features in [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)].</span></span> <span data-ttu-id="8768b-105">Aby uzyskać więcej informacji, [Zobacz optymistyczne współbieżność: Przegląd](../../../../../../docs/framework/data/adonet/sql/linq/optimistic-concurrency-overview.md).</span><span class="sxs-lookup"><span data-stu-id="8768b-105">For more information, see [Optimistic Concurrency: Overview](../../../../../../docs/framework/data/adonet/sql/linq/optimistic-concurrency-overview.md).</span></span>  
  
> [!NOTE]
> <span data-ttu-id="8768b-106">Pierwotne wartości elementów członkowskich są porównywane z bieżącym stanem bazy danych, o ile nie `IsVersion=true`wyznaczono żadnego elementu członkowskiego.</span><span class="sxs-lookup"><span data-stu-id="8768b-106">Original member values are compared with the current database state as long as no member is designated as `IsVersion=true`.</span></span> <span data-ttu-id="8768b-107">Aby uzyskać więcej informacji, zobacz <xref:System.Data.Linq.Mapping.ColumnAttribute.IsVersion%2A>.</span><span class="sxs-lookup"><span data-stu-id="8768b-107">For more information, see <xref:System.Data.Linq.Mapping.ColumnAttribute.IsVersion%2A>.</span></span>  
  
 <span data-ttu-id="8768b-108">Aby zapoznać się z przykładami kodu, zobacz <xref:System.Data.Linq.Mapping.ColumnAttribute.UpdateCheck%2A>.</span><span class="sxs-lookup"><span data-stu-id="8768b-108">For code examples, see <xref:System.Data.Linq.Mapping.ColumnAttribute.UpdateCheck%2A>.</span></span>  
  
### <a name="to-always-use-this-member-for-detecting-conflicts"></a><span data-ttu-id="8768b-109">Aby zawsze używać tego elementu członkowskiego do wykrywania konfliktów</span><span class="sxs-lookup"><span data-stu-id="8768b-109">To always use this member for detecting conflicts</span></span>  
  
1. <span data-ttu-id="8768b-110"><xref:System.Data.Linq.Mapping.ColumnAttribute.UpdateCheck%2A> Dodaj Właściwość<xref:System.Data.Linq.Mapping.ColumnAttribute> do atrybutu.</span><span class="sxs-lookup"><span data-stu-id="8768b-110">Add the <xref:System.Data.Linq.Mapping.ColumnAttribute.UpdateCheck%2A> property to the <xref:System.Data.Linq.Mapping.ColumnAttribute> attribute.</span></span>  
  
2. <span data-ttu-id="8768b-111">`Always`Ustaw wartość <xref:System.Data.Linq.Mapping.ColumnAttribute.UpdateCheck%2A> właściwości na.</span><span class="sxs-lookup"><span data-stu-id="8768b-111">Set the <xref:System.Data.Linq.Mapping.ColumnAttribute.UpdateCheck%2A> property value to `Always`.</span></span>  
  
### <a name="to-never-use-this-member-for-detecting-conflicts"></a><span data-ttu-id="8768b-112">Aby nigdy nie używać tego elementu członkowskiego do wykrywania konfliktów</span><span class="sxs-lookup"><span data-stu-id="8768b-112">To never use this member for detecting conflicts</span></span>  
  
1. <span data-ttu-id="8768b-113"><xref:System.Data.Linq.Mapping.ColumnAttribute.UpdateCheck%2A> Dodaj Właściwość<xref:System.Data.Linq.Mapping.ColumnAttribute> do atrybutu.</span><span class="sxs-lookup"><span data-stu-id="8768b-113">Add the <xref:System.Data.Linq.Mapping.ColumnAttribute.UpdateCheck%2A> property to the <xref:System.Data.Linq.Mapping.ColumnAttribute> attribute.</span></span>  
  
2. <span data-ttu-id="8768b-114">`Never`Ustaw wartość <xref:System.Data.Linq.Mapping.ColumnAttribute.UpdateCheck%2A> właściwości na.</span><span class="sxs-lookup"><span data-stu-id="8768b-114">Set the <xref:System.Data.Linq.Mapping.ColumnAttribute.UpdateCheck%2A> property value to `Never`.</span></span>  
  
### <a name="to-use-this-member-for-detecting-conflicts-only-when-the-application-has-changed-the-value-of-the-member"></a><span data-ttu-id="8768b-115">Aby użyć tego elementu członkowskiego do wykrywania konfliktów tylko wtedy, gdy aplikacja zmieniła wartość elementu członkowskiego</span><span class="sxs-lookup"><span data-stu-id="8768b-115">To use this member for detecting conflicts only when the application has changed the value of the member</span></span>  
  
1. <span data-ttu-id="8768b-116"><xref:System.Data.Linq.Mapping.ColumnAttribute.UpdateCheck%2A> Dodaj Właściwość<xref:System.Data.Linq.Mapping.ColumnAttribute> do atrybutu.</span><span class="sxs-lookup"><span data-stu-id="8768b-116">Add the <xref:System.Data.Linq.Mapping.ColumnAttribute.UpdateCheck%2A> property to the <xref:System.Data.Linq.Mapping.ColumnAttribute> attribute.</span></span>  
  
2. <span data-ttu-id="8768b-117">`WhenChanged`Ustaw wartość <xref:System.Data.Linq.Mapping.ColumnAttribute.UpdateCheck%2A> właściwości na.</span><span class="sxs-lookup"><span data-stu-id="8768b-117">Set the <xref:System.Data.Linq.Mapping.ColumnAttribute.UpdateCheck%2A> property value to `WhenChanged`.</span></span>  
  
## <a name="example"></a><span data-ttu-id="8768b-118">Przykład</span><span class="sxs-lookup"><span data-stu-id="8768b-118">Example</span></span>  
 <span data-ttu-id="8768b-119">W poniższym przykładzie określono, `HomePage` że obiekty nigdy nie powinny być testowane podczas sprawdzania aktualizacji.</span><span class="sxs-lookup"><span data-stu-id="8768b-119">The following example specifies that `HomePage` objects should never be tested during update checks.</span></span> <span data-ttu-id="8768b-120">Aby uzyskać więcej informacji, zobacz <xref:System.Data.Linq.Mapping.ColumnAttribute.UpdateCheck%2A>.</span><span class="sxs-lookup"><span data-stu-id="8768b-120">For more information, see <xref:System.Data.Linq.Mapping.ColumnAttribute.UpdateCheck%2A>.</span></span>  
  
 [!code-csharp[System.Data.Linq.Mapping.UpdateCheck#1](../../../../../../samples/snippets/csharp/VS_Snippets_Data/system.data.linq.mapping.updatecheck/cs/northwind.cs#1)]
 [!code-vb[System.Data.Linq.Mapping.UpdateCheck#1](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/system.data.linq.mapping.updatecheck/vb/northwind.vb#1)]  
  
## <a name="see-also"></a><span data-ttu-id="8768b-121">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="8768b-121">See also</span></span>

- [<span data-ttu-id="8768b-122">Instrukcje: Zarządzanie konfliktami zmian</span><span class="sxs-lookup"><span data-stu-id="8768b-122">How to: Manage Change Conflicts</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/how-to-manage-change-conflicts.md)
- [<span data-ttu-id="8768b-123">Tworzenie i przesyłanie zmian danych</span><span class="sxs-lookup"><span data-stu-id="8768b-123">Making and Submitting Data Changes</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/making-and-submitting-data-changes.md)

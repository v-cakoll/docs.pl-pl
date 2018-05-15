---
title: 'Porady: Określanie, które elementy członkowskie są sprawdzane pod kątem konfliktom współbieżności'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: d2cda293-1e2f-4878-af0e-5aaf0d092120
ms.openlocfilehash: 7cabd8c799db4979642c462803df323d13139547
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="how-to-specify-which-members-are-tested-for-concurrency-conflicts"></a><span data-ttu-id="1b808-102">Porady: Określanie, które elementy członkowskie są sprawdzane pod kątem konfliktom współbieżności</span><span class="sxs-lookup"><span data-stu-id="1b808-102">How to: Specify Which Members are Tested for Concurrency Conflicts</span></span>
<span data-ttu-id="1b808-103">Zastosuj jedną z trzech typów wyliczeniowych do [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] <xref:System.Data.Linq.Mapping.ColumnAttribute.UpdateCheck%2A> właściwość <xref:System.Data.Linq.Mapping.ColumnAttribute> atrybutu, aby określić, którzy członkowie mają być uwzględniane w aktualizacji sprawdza wykrywanie konfliktów optymistycznej współbieżności.</span><span class="sxs-lookup"><span data-stu-id="1b808-103">Apply one of three enums to the [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] <xref:System.Data.Linq.Mapping.ColumnAttribute.UpdateCheck%2A> property on a <xref:System.Data.Linq.Mapping.ColumnAttribute> attribute to specify which members are to be included in update checks for the detection of optimistic concurrency conflicts.</span></span>  
  
 <span data-ttu-id="1b808-104"><xref:System.Data.Linq.Mapping.ColumnAttribute.UpdateCheck%2A> (Zamapować w czasie projektowania) jest używana razem z funkcji współbieżności środowiska wykonawczego w [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)].</span><span class="sxs-lookup"><span data-stu-id="1b808-104">The <xref:System.Data.Linq.Mapping.ColumnAttribute.UpdateCheck%2A> property (mapped at design time) is used together with run-time concurrency features in [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)].</span></span> <span data-ttu-id="1b808-105">Aby uzyskać więcej informacji, zobacz [optymistycznej współbieżności: omówienie](../../../../../../docs/framework/data/adonet/sql/linq/optimistic-concurrency-overview.md).</span><span class="sxs-lookup"><span data-stu-id="1b808-105">For more information, see [Optimistic Concurrency: Overview](../../../../../../docs/framework/data/adonet/sql/linq/optimistic-concurrency-overview.md).</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="1b808-106">Oryginalne wartości elementu członkowskiego są porównywane z bieżącym stanem bazy danych, tak długo, jak żaden element członkowski jest oznaczony jako `IsVersion=true`.</span><span class="sxs-lookup"><span data-stu-id="1b808-106">Original member values are compared with the current database state as long as no member is designated as `IsVersion=true`.</span></span> <span data-ttu-id="1b808-107">Aby uzyskać więcej informacji, zobacz <xref:System.Data.Linq.Mapping.ColumnAttribute.IsVersion%2A>.</span><span class="sxs-lookup"><span data-stu-id="1b808-107">For more information, see <xref:System.Data.Linq.Mapping.ColumnAttribute.IsVersion%2A>.</span></span>  
  
 <span data-ttu-id="1b808-108">Aby uzyskać przykłady kodu, zobacz <xref:System.Data.Linq.Mapping.ColumnAttribute.UpdateCheck%2A>.</span><span class="sxs-lookup"><span data-stu-id="1b808-108">For code examples, see <xref:System.Data.Linq.Mapping.ColumnAttribute.UpdateCheck%2A>.</span></span>  
  
### <a name="to-always-use-this-member-for-detecting-conflicts"></a><span data-ttu-id="1b808-109">Zawsze używaj tego elementu członkowskiego do wykrywania konfliktów</span><span class="sxs-lookup"><span data-stu-id="1b808-109">To always use this member for detecting conflicts</span></span>  
  
1.  <span data-ttu-id="1b808-110">Dodaj <xref:System.Data.Linq.Mapping.ColumnAttribute.UpdateCheck%2A> właściwości <xref:System.Data.Linq.Mapping.ColumnAttribute> atrybutu.</span><span class="sxs-lookup"><span data-stu-id="1b808-110">Add the <xref:System.Data.Linq.Mapping.ColumnAttribute.UpdateCheck%2A> property to the <xref:System.Data.Linq.Mapping.ColumnAttribute> attribute.</span></span>  
  
2.  <span data-ttu-id="1b808-111">Ustaw <xref:System.Data.Linq.Mapping.ColumnAttribute.UpdateCheck%2A> wartości właściwości do `Always`.</span><span class="sxs-lookup"><span data-stu-id="1b808-111">Set the <xref:System.Data.Linq.Mapping.ColumnAttribute.UpdateCheck%2A> property value to `Always`.</span></span>  
  
### <a name="to-never-use-this-member-for-detecting-conflicts"></a><span data-ttu-id="1b808-112">Nigdy nie należy używać tego elementu członkowskiego do wykrywania konfliktów</span><span class="sxs-lookup"><span data-stu-id="1b808-112">To never use this member for detecting conflicts</span></span>  
  
1.  <span data-ttu-id="1b808-113">Dodaj <xref:System.Data.Linq.Mapping.ColumnAttribute.UpdateCheck%2A> właściwości <xref:System.Data.Linq.Mapping.ColumnAttribute> atrybutu.</span><span class="sxs-lookup"><span data-stu-id="1b808-113">Add the <xref:System.Data.Linq.Mapping.ColumnAttribute.UpdateCheck%2A> property to the <xref:System.Data.Linq.Mapping.ColumnAttribute> attribute.</span></span>  
  
2.  <span data-ttu-id="1b808-114">Ustaw <xref:System.Data.Linq.Mapping.ColumnAttribute.UpdateCheck%2A> wartości właściwości do `Never`.</span><span class="sxs-lookup"><span data-stu-id="1b808-114">Set the <xref:System.Data.Linq.Mapping.ColumnAttribute.UpdateCheck%2A> property value to `Never`.</span></span>  
  
### <a name="to-use-this-member-for-detecting-conflicts-only-when-the-application-has-changed-the-value-of-the-member"></a><span data-ttu-id="1b808-115">Aby użyć tego elementu członkowskiego do wykrywania konfliktów tylko wtedy, gdy aplikacja została zmieniona wartość elementu członkowskiego</span><span class="sxs-lookup"><span data-stu-id="1b808-115">To use this member for detecting conflicts only when the application has changed the value of the member</span></span>  
  
1.  <span data-ttu-id="1b808-116">Dodaj <xref:System.Data.Linq.Mapping.ColumnAttribute.UpdateCheck%2A> właściwości <xref:System.Data.Linq.Mapping.ColumnAttribute> atrybutu.</span><span class="sxs-lookup"><span data-stu-id="1b808-116">Add the <xref:System.Data.Linq.Mapping.ColumnAttribute.UpdateCheck%2A> property to the <xref:System.Data.Linq.Mapping.ColumnAttribute> attribute.</span></span>  
  
2.  <span data-ttu-id="1b808-117">Ustaw <xref:System.Data.Linq.Mapping.ColumnAttribute.UpdateCheck%2A> wartości właściwości do `WhenChanged`.</span><span class="sxs-lookup"><span data-stu-id="1b808-117">Set the <xref:System.Data.Linq.Mapping.ColumnAttribute.UpdateCheck%2A> property value to `WhenChanged`.</span></span>  
  
## <a name="example"></a><span data-ttu-id="1b808-118">Przykład</span><span class="sxs-lookup"><span data-stu-id="1b808-118">Example</span></span>  
 <span data-ttu-id="1b808-119">Poniższy przykład określa, że `HomePage` obiekty nigdy nie należy podawać podczas sprawdzania aktualizacji.</span><span class="sxs-lookup"><span data-stu-id="1b808-119">The following example specifies that `HomePage` objects should never be tested during update checks.</span></span> <span data-ttu-id="1b808-120">Aby uzyskać więcej informacji, zobacz <xref:System.Data.Linq.Mapping.ColumnAttribute.UpdateCheck%2A>.</span><span class="sxs-lookup"><span data-stu-id="1b808-120">For more information, see <xref:System.Data.Linq.Mapping.ColumnAttribute.UpdateCheck%2A>.</span></span>  
  
 [!code-csharp[System.Data.Linq.Mapping.UpdateCheck#1](../../../../../../samples/snippets/csharp/VS_Snippets_Data/system.data.linq.mapping.updatecheck/cs/northwind.cs#1)]
 [!code-vb[System.Data.Linq.Mapping.UpdateCheck#1](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/system.data.linq.mapping.updatecheck/vb/northwind.vb#1)]  
  
## <a name="see-also"></a><span data-ttu-id="1b808-121">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="1b808-121">See Also</span></span>  
 [<span data-ttu-id="1b808-122">Instrukcje: Zarządzanie konfliktami zmian</span><span class="sxs-lookup"><span data-stu-id="1b808-122">How to: Manage Change Conflicts</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/how-to-manage-change-conflicts.md)  
 [<span data-ttu-id="1b808-123">Tworzenie i przesyłanie zmian danych</span><span class="sxs-lookup"><span data-stu-id="1b808-123">Making and Submitting Data Changes</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/making-and-submitting-data-changes.md)

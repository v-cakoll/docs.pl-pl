---
title: Rozpoznanie późnego wiązania; mogą wystąpić błędy podczas wykonywania
ms.date: 07/20/2015
f1_keywords:
- vbc42017
- BC42017
helpviewer_keywords:
- BC42017
ms.assetid: 45f552c8-57c6-44c0-97d3-e510119b257a
ms.openlocfilehash: 4fe79c74b6ff634223a4f10d8c5dc54bb77571cc
ms.sourcegitcommit: bce0586f0cccaae6d6cbd625d5a7b824d1d3de4b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/02/2019
ms.locfileid: "58822294"
---
# <a name="late-bound-resolution-runtime-errors-could-occur"></a><span data-ttu-id="84e84-102">Rozpoznanie późnego wiązania; mogą wystąpić błędy podczas wykonywania</span><span class="sxs-lookup"><span data-stu-id="84e84-102">Late bound resolution; runtime errors could occur</span></span>
<span data-ttu-id="84e84-103">Obiekt jest przypisany do zmiennej, zadeklarowanej będzie [Object — typ danych](../../../visual-basic/language-reference/data-types/object-data-type.md).</span><span class="sxs-lookup"><span data-stu-id="84e84-103">An object is assigned to a variable declared to be of the [Object Data Type](../../../visual-basic/language-reference/data-types/object-data-type.md).</span></span>  
  
 <span data-ttu-id="84e84-104">Kiedy Deklarujesz zmienną `Object`, kompilator musi wykonać *późnym wiązaniu*, co powoduje, że dodatkowe operacje w czasie wykonywania.</span><span class="sxs-lookup"><span data-stu-id="84e84-104">When you declare a variable as `Object`, the compiler must perform *late binding*, which causes extra operations at run time.</span></span> <span data-ttu-id="84e84-105">Udostępnia ona również aplikację, aby potencjalne błędy czasu wykonywania.</span><span class="sxs-lookup"><span data-stu-id="84e84-105">It also exposes your application to potential run-time errors.</span></span> <span data-ttu-id="84e84-106">Na przykład, jeśli przypisujesz <xref:System.Windows.Forms.Form> do `Object` zmiennej, a następnie spróbuj uzyskać dostęp do <xref:System.Xml.XmlDocument.NameTable%2A?displayProperty=nameWithType> właściwości, środowisko wykonawcze zgłasza <xref:System.MemberAccessException> ponieważ <xref:System.Windows.Forms.Form> klasy nie ujawnia `NameTable` właściwości.</span><span class="sxs-lookup"><span data-stu-id="84e84-106">For example, if you assign a <xref:System.Windows.Forms.Form> to the `Object` variable and then try to access the <xref:System.Xml.XmlDocument.NameTable%2A?displayProperty=nameWithType> property, the runtime throws a <xref:System.MemberAccessException> because the <xref:System.Windows.Forms.Form> class does not expose a `NameTable` property.</span></span>  
  
 <span data-ttu-id="84e84-107">Jeśli zadeklarujesz zmienną określonego typu, kompilator będzie mógł wykonać *wczesne powiązania* w czasie kompilacji.</span><span class="sxs-lookup"><span data-stu-id="84e84-107">If you declare the variable to be of a specific type, the compiler can perform *early binding* at compile time.</span></span> <span data-ttu-id="84e84-108">Skutkuje to lepszą wydajność i kontrolowany dostęp do elementów członkowskich z określonego typu i zwiększenia czytelności kodu.</span><span class="sxs-lookup"><span data-stu-id="84e84-108">This results in improved performance, controlled access to the members of the specific type, and better readability of your code.</span></span>  
  
 <span data-ttu-id="84e84-109">Domyślnie ta wiadomość jest ostrzeżenie.</span><span class="sxs-lookup"><span data-stu-id="84e84-109">By default, this message is a warning.</span></span> <span data-ttu-id="84e84-110">Uzyskać informacje o ukrywaniu ostrzeżenia lub traktowanie ostrzeżeń jako błędy, zobacz [Konfigurowanie ostrzeżeń w języku Visual Basic](/visualstudio/ide/configuring-warnings-in-visual-basic).</span><span class="sxs-lookup"><span data-stu-id="84e84-110">For information on hiding warnings or treating warnings as errors, see [Configuring Warnings in Visual Basic](/visualstudio/ide/configuring-warnings-in-visual-basic).</span></span>  
  
 <span data-ttu-id="84e84-111">**Identyfikator błędu:** BC42017</span><span class="sxs-lookup"><span data-stu-id="84e84-111">**Error ID:** BC42017</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="84e84-112">Aby poprawić ten błąd</span><span class="sxs-lookup"><span data-stu-id="84e84-112">To correct this error</span></span>  
  
-   <span data-ttu-id="84e84-113">Jeśli to możliwe należy zadeklarować zmienną określonego typu.</span><span class="sxs-lookup"><span data-stu-id="84e84-113">If possible, declare the variable to be of a specific type.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="84e84-114">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="84e84-114">See also</span></span>

- [<span data-ttu-id="84e84-115">Wczesne i późne powiązania</span><span class="sxs-lookup"><span data-stu-id="84e84-115">Early and Late Binding</span></span>](../../../visual-basic/programming-guide/language-features/early-late-binding/index.md)
- [<span data-ttu-id="84e84-116">Deklaracja zmiennej obiektu</span><span class="sxs-lookup"><span data-stu-id="84e84-116">Object Variable Declaration</span></span>](../../../visual-basic/programming-guide/language-features/variables/object-variable-declaration.md)

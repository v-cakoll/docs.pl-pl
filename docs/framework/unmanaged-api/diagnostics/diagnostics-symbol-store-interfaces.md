---
title: Interfejsy magazynu symboli diagnostycznych
ms.date: 03/30/2017
helpviewer_keywords:
- unmanaged interfaces [.NET Framework], debugging
- diagnostics symbol store interfaces [.NET Framework]
- interfaces [.NET Framework], diagnostics symbol store
- unmanaged interfaces [.NET Framework], diagnostics symbol store
- debugging interfaces [.NET Framework]
- interfaces [.NET Framework debugging]
ms.assetid: f96987d5-e6a5-478b-ac5e-302e16545cce
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 6fca7359888b8b73b2e1cf709ab708d71abf0db6
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61787897"
---
# <a name="diagnostics-symbol-store-interfaces"></a><span data-ttu-id="42fe2-102">Interfejsy magazynu symboli diagnostycznych</span><span class="sxs-lookup"><span data-stu-id="42fe2-102">Diagnostics Symbol Store Interfaces</span></span>
<span data-ttu-id="42fe2-103">W tym temacie opisano niezarządzane interfejsy, które umożliwiają kompilatora do generowania informacji o symbolach do użytku przez debuger.</span><span class="sxs-lookup"><span data-stu-id="42fe2-103">This topic describes the unmanaged interfaces that enable a compiler to generate symbol information for use by a debugger.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="42fe2-104">W tej sekcji</span><span class="sxs-lookup"><span data-stu-id="42fe2-104">In This Section</span></span>  
 [<span data-ttu-id="42fe2-105">IBindingDisplay, interfejs</span><span class="sxs-lookup"><span data-stu-id="42fe2-105">IBindingDisplay Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/ibindingdisplay-interface.md)  
 <span data-ttu-id="42fe2-106">Udostępnia metody, które wyświetlają bieżące informacje o powiązaniu o uruchomionej aplikacji.</span><span class="sxs-lookup"><span data-stu-id="42fe2-106">Provides methods that display current binding information about the running application.</span></span>  
  
 [<span data-ttu-id="42fe2-107">IDebugAutoAttach, interfejs</span><span class="sxs-lookup"><span data-stu-id="42fe2-107">IDebugAutoAttach Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/idebugautoattach-interface.md)  
 <span data-ttu-id="42fe2-108">Definiuje interfejs dla automatycznego wywoływane serwer debugera dołączania.</span><span class="sxs-lookup"><span data-stu-id="42fe2-108">Defines the interface for a server-invoked debugger auto attach.</span></span>  
  
 [<span data-ttu-id="42fe2-109">INotifyConnection2, interfejs</span><span class="sxs-lookup"><span data-stu-id="42fe2-109">INotifyConnection2 Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/inotifyconnection2-interface.md)  
 <span data-ttu-id="42fe2-110">Deklaruje metody zarejestrować lub wyrejestrować źródła powiadomień połączenia.</span><span class="sxs-lookup"><span data-stu-id="42fe2-110">Declares methods for registering and unregistering a connection notification source.</span></span>  
  
 [<span data-ttu-id="42fe2-111">INotifySink2, interfejs</span><span class="sxs-lookup"><span data-stu-id="42fe2-111">INotifySink2 Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/inotifysink2-interface.md)  
 <span data-ttu-id="42fe2-112">Deklaruje metody dla obiektu sink powiadomień.</span><span class="sxs-lookup"><span data-stu-id="42fe2-112">Declares methods for sink notification.</span></span>  
  
 [<span data-ttu-id="42fe2-113">INotifySource2, interfejs</span><span class="sxs-lookup"><span data-stu-id="42fe2-113">INotifySource2 Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/inotifysource2-interface.md)  
 <span data-ttu-id="42fe2-114">Deklaruje metody do ustawiania filtrów powiadomień.</span><span class="sxs-lookup"><span data-stu-id="42fe2-114">Declares a method for setting notification filters.</span></span>  
  
 [<span data-ttu-id="42fe2-115">ISymENCUnmanagedMethod, interfejs</span><span class="sxs-lookup"><span data-stu-id="42fe2-115">ISymENCUnmanagedMethod Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymencunmanagedmethod-interface.md)  
 <span data-ttu-id="42fe2-116">Informacje dotyczące funkcji Edytuj i Kontynuuj.</span><span class="sxs-lookup"><span data-stu-id="42fe2-116">Provides information for the Edit and Continue feature.</span></span>  
  
 [<span data-ttu-id="42fe2-117">ISymUnmanagedAsyncMethod, interfejs</span><span class="sxs-lookup"><span data-stu-id="42fe2-117">ISymUnmanagedAsyncMethod Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedasyncmethod-interface.md)  
 <span data-ttu-id="42fe2-118">Ten interfejs jest to uzupełnienie odczytu [ISymUnmanagedAsyncMethodPropertiesWriter, interfejs](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedasyncmethodpropertieswriter-interface.md).</span><span class="sxs-lookup"><span data-stu-id="42fe2-118">This interface is the reading complement to [ISymUnmanagedAsyncMethodPropertiesWriter Interface](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedasyncmethodpropertieswriter-interface.md).</span></span>  
  
 [<span data-ttu-id="42fe2-119">ISymUnmanagedAsyncMethodPropertiesWriter, interfejs</span><span class="sxs-lookup"><span data-stu-id="42fe2-119">ISymUnmanagedAsyncMethodPropertiesWriter Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedasyncmethodpropertieswriter-interface.md)  
 <span data-ttu-id="42fe2-120">Pozwala na określenie informacji o metodzie async opcjonalne na symbol metody.</span><span class="sxs-lookup"><span data-stu-id="42fe2-120">Allows definition of optional async method information per method symbol.</span></span> <span data-ttu-id="42fe2-121">Należy używać z metodą otwarte (to znaczy między wywołaniami [openmethod — metoda](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-openmethod-method.md)i [closemethod — metoda](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-closemethod-method.md)).</span><span class="sxs-lookup"><span data-stu-id="42fe2-121">Must use with an opened method (that is, between calls to the [OpenMethod Method](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-openmethod-method.md)and the [CloseMethod Method](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-closemethod-method.md)).</span></span>  
  
 [<span data-ttu-id="42fe2-122">ISymUnmanagedBinder, interfejs</span><span class="sxs-lookup"><span data-stu-id="42fe2-122">ISymUnmanagedBinder Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedbinder-interface.md)  
 <span data-ttu-id="42fe2-123">Reprezentuje integrator symboli dla niezarządzanego kodu.</span><span class="sxs-lookup"><span data-stu-id="42fe2-123">Represents a symbol binder for unmanaged code.</span></span>  
  
 [<span data-ttu-id="42fe2-124">ISymUnmanagedBinder2, interfejs</span><span class="sxs-lookup"><span data-stu-id="42fe2-124">ISymUnmanagedBinder2 Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedbinder2-interface.md)  
 <span data-ttu-id="42fe2-125">Reprezentuje integrator symboli dla niezarządzanego kodu i rozszerza `ISymUnmanagedBinder` interfejsu.</span><span class="sxs-lookup"><span data-stu-id="42fe2-125">Represents a symbol binder for unmanaged code, and extends the `ISymUnmanagedBinder` interface.</span></span>  
  
 [<span data-ttu-id="42fe2-126">ISymUnmanagedBinder3, interfejs</span><span class="sxs-lookup"><span data-stu-id="42fe2-126">ISymUnmanagedBinder3 Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedbinder3-interface.md)  
 <span data-ttu-id="42fe2-127">Reprezentuje integrator symboli dla niezarządzanego kodu i rozszerza `ISymUnmanagedBinder` interfejsu.</span><span class="sxs-lookup"><span data-stu-id="42fe2-127">Represents a symbol binder for unmanaged code, and extends the `ISymUnmanagedBinder` interface.</span></span>  
  
 [<span data-ttu-id="42fe2-128">ISymUnmanagedConstant, interfejs</span><span class="sxs-lookup"><span data-stu-id="42fe2-128">ISymUnmanagedConstant Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedconstant-interface.md)  
 <span data-ttu-id="42fe2-129">Zapewnia dostęp do niezarządzanego stałych.</span><span class="sxs-lookup"><span data-stu-id="42fe2-129">Provides access to unmanaged constants.</span></span>  
  
 [<span data-ttu-id="42fe2-130">ISymUnmanagedDispose, interfejs</span><span class="sxs-lookup"><span data-stu-id="42fe2-130">ISymUnmanagedDispose Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanageddispose-interface.md)  
 <span data-ttu-id="42fe2-131">Usuwa zasoby niezarządzane.</span><span class="sxs-lookup"><span data-stu-id="42fe2-131">Disposes of unmanaged resources.</span></span>  
  
 [<span data-ttu-id="42fe2-132">ISymUnmanagedDocument, interfejs</span><span class="sxs-lookup"><span data-stu-id="42fe2-132">ISymUnmanagedDocument Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanageddocument-interface.md)  
 <span data-ttu-id="42fe2-133">Reprezentuje dokument odwołuje się w magazynie symboli.</span><span class="sxs-lookup"><span data-stu-id="42fe2-133">Represents a document referenced by a symbol store.</span></span>  
  
 [<span data-ttu-id="42fe2-134">ISymUnmanagedDocumentWriter, interfejs</span><span class="sxs-lookup"><span data-stu-id="42fe2-134">ISymUnmanagedDocumentWriter Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanageddocumentwriter-interface.md)  
 <span data-ttu-id="42fe2-135">Udostępnia metody do zapisywania dokumentu odwołuje się w magazynie symboli.</span><span class="sxs-lookup"><span data-stu-id="42fe2-135">Provides methods for writing to a document referenced by a symbol store.</span></span>  
  
 [<span data-ttu-id="42fe2-136">ISymUnmanagedENCUpdate, interfejs</span><span class="sxs-lookup"><span data-stu-id="42fe2-136">ISymUnmanagedENCUpdate Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedencupdate-interface.md)  
 <span data-ttu-id="42fe2-137">Udostępnia metody dla funkcji Edytuj i Kontynuuj.</span><span class="sxs-lookup"><span data-stu-id="42fe2-137">Provides methods for the Edit and Continue feature.</span></span>  
  
 [<span data-ttu-id="42fe2-138">ISymUnmanagedMethod, interfejs</span><span class="sxs-lookup"><span data-stu-id="42fe2-138">ISymUnmanagedMethod Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedmethod-interface.md)  
 <span data-ttu-id="42fe2-139">Reprezentuje metodę w magazynie symboli.</span><span class="sxs-lookup"><span data-stu-id="42fe2-139">Represents a method within the symbol store.</span></span>  
  
 [<span data-ttu-id="42fe2-140">ISymUnmanagedNamespace, interfejs</span><span class="sxs-lookup"><span data-stu-id="42fe2-140">ISymUnmanagedNamespace Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagednamespace-interface.md)  
 <span data-ttu-id="42fe2-141">Reprezentuje obszar nazw.</span><span class="sxs-lookup"><span data-stu-id="42fe2-141">Represents a namespace.</span></span>  
  
 [<span data-ttu-id="42fe2-142">ISymUnmanagedReader, interfejs</span><span class="sxs-lookup"><span data-stu-id="42fe2-142">ISymUnmanagedReader Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedreader-interface.md)  
 <span data-ttu-id="42fe2-143">Reprezentuje czytnik symbolu, który zapewnia dostęp do dokumentów, metod i zmiennych w magazynie symboli.</span><span class="sxs-lookup"><span data-stu-id="42fe2-143">Represents a symbol reader that provides access to documents, methods, and variables within a symbol store.</span></span>  
  
 [<span data-ttu-id="42fe2-144">ISymUnmanagedReader2, interfejs</span><span class="sxs-lookup"><span data-stu-id="42fe2-144">ISymUnmanagedReader2 Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedreader2-interface.md)  
 <span data-ttu-id="42fe2-145">Pobiera metodę czytnika symboli podany token metody i numeru wersji edycji i kopiowania.</span><span class="sxs-lookup"><span data-stu-id="42fe2-145">Gets a symbol reader method given a method token and an edit-and-copy version number.</span></span>  
  
 [<span data-ttu-id="42fe2-146">ISymUnmanagedReaderSymbolSearchInfo, interfejs</span><span class="sxs-lookup"><span data-stu-id="42fe2-146">ISymUnmanagedReaderSymbolSearchInfo Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedreadersymbolsearchinfo-interface.md)  
 <span data-ttu-id="42fe2-147">Udostępnia metody, które zawierają informacje o wyszukiwaniu symboli.</span><span class="sxs-lookup"><span data-stu-id="42fe2-147">Provides methods that get symbol search information.</span></span>  
  
 [<span data-ttu-id="42fe2-148">ISymUnmanagedScope, interfejs</span><span class="sxs-lookup"><span data-stu-id="42fe2-148">ISymUnmanagedScope Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedscope-interface.md)  
 <span data-ttu-id="42fe2-149">Reprezentuje zakresie leksykalnym wewnątrz metody.</span><span class="sxs-lookup"><span data-stu-id="42fe2-149">Represents a lexical scope within a method.</span></span>  
  
 [<span data-ttu-id="42fe2-150">ISymUnmanagedScope2, interfejs</span><span class="sxs-lookup"><span data-stu-id="42fe2-150">ISymUnmanagedScope2 Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedscope2-interface.md)  
 <span data-ttu-id="42fe2-151">Reprezentuje zakresie leksykalnym wewnątrz metody i rozszerza `ISymUnmanagedScope` interfejs, za pomocą metod, które uzyskać informacje na temat stałe zdefiniowane w zakresie...</span><span class="sxs-lookup"><span data-stu-id="42fe2-151">Represents a lexical scope within a method, and extends the `ISymUnmanagedScope` interface with methods that get information about constants defined within the scope..</span></span>  
  
 [<span data-ttu-id="42fe2-152">ISymUnmanagedSourceServerModule, interfejs</span><span class="sxs-lookup"><span data-stu-id="42fe2-152">ISymUnmanagedSourceServerModule Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedsourceservermodule-interface.md)  
 <span data-ttu-id="42fe2-153">Udostępnia dane z serwera źródłowego dla modułu.</span><span class="sxs-lookup"><span data-stu-id="42fe2-153">Provides source server data for a module.</span></span>  
  
 [<span data-ttu-id="42fe2-154">ISymUnmanagedSymbolSearchInfo, interfejs</span><span class="sxs-lookup"><span data-stu-id="42fe2-154">ISymUnmanagedSymbolSearchInfo Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedsymbolsearchinfo-interface.md)  
 <span data-ttu-id="42fe2-155">Udostępnia metody, które zawierają informacje o ścieżce wyszukiwania.</span><span class="sxs-lookup"><span data-stu-id="42fe2-155">Provides methods that get information about the search path.</span></span>  
  
 [<span data-ttu-id="42fe2-156">ISymUnmanagedVariable, interfejs</span><span class="sxs-lookup"><span data-stu-id="42fe2-156">ISymUnmanagedVariable Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedvariable-interface.md)  
 <span data-ttu-id="42fe2-157">Reprezentuje zmienną, takie jak parametr, zmienna lokalna lub pola.</span><span class="sxs-lookup"><span data-stu-id="42fe2-157">Represents a variable, such as a parameter, a local variable, or a field.</span></span>  
  
 [<span data-ttu-id="42fe2-158">ISymUnmanagedWriter, interfejs</span><span class="sxs-lookup"><span data-stu-id="42fe2-158">ISymUnmanagedWriter Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-interface.md)  
 <span data-ttu-id="42fe2-159">Reprezentuje edytor symboli i zapewnia metody do definiowania dokumentów, punktów sekwencji, leksykalne zakresy i zmienne.</span><span class="sxs-lookup"><span data-stu-id="42fe2-159">Represents a symbol writer, and provides methods to define documents, sequence points, lexical scopes, and variables.</span></span>  
  
 [<span data-ttu-id="42fe2-160">ISymUnmanagedWriter2, interfejs</span><span class="sxs-lookup"><span data-stu-id="42fe2-160">ISymUnmanagedWriter2 Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter2-interface.md)  
 <span data-ttu-id="42fe2-161">Reprezentuje edytor symboli i zapewnia metody do definiowania dokumentów, punktów sekwencji, leksykalne zakresy i zmienne.</span><span class="sxs-lookup"><span data-stu-id="42fe2-161">Represents a symbol writer, and provides methods to define documents, sequence points, lexical scopes, and variables.</span></span> <span data-ttu-id="42fe2-162">Rozszerza `ISymUnmanagedWriter` interfejsu.</span><span class="sxs-lookup"><span data-stu-id="42fe2-162">Extends the `ISymUnmanagedWriter` interface.</span></span>  
  
 [<span data-ttu-id="42fe2-163">ISymUnmanagedWriter3, interfejs</span><span class="sxs-lookup"><span data-stu-id="42fe2-163">ISymUnmanagedWriter3 Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter3-interface.md)  
 <span data-ttu-id="42fe2-164">Reprezentuje edytor symboli i zapewnia metody do definiowania dokumentów, punktów sekwencji, leksykalne zakresy i zmienne.</span><span class="sxs-lookup"><span data-stu-id="42fe2-164">Represents a symbol writer, and provides methods to define documents, sequence points, lexical scopes, and variables.</span></span> <span data-ttu-id="42fe2-165">Rozszerza `ISymUnmanagedWriter` interfejsu.</span><span class="sxs-lookup"><span data-stu-id="42fe2-165">Extends the `ISymUnmanagedWriter` interface.</span></span>  
  
 [<span data-ttu-id="42fe2-166">ISymUnmanagedWriter4, interfejs</span><span class="sxs-lookup"><span data-stu-id="42fe2-166">ISymUnmanagedWriter4 Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter4-interface.md)  
 <span data-ttu-id="42fe2-167">ISymUnmanagedWriter4, interfejs</span><span class="sxs-lookup"><span data-stu-id="42fe2-167">ISymUnmanagedWriter4 interface.</span></span>  
  
 [<span data-ttu-id="42fe2-168">ISymUnmanagedWriter5, interfejs</span><span class="sxs-lookup"><span data-stu-id="42fe2-168">ISymUnmanagedWriter5 Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter5-interface.md)  
 <span data-ttu-id="42fe2-169">ISymUnmanagedWriter5, interfejs</span><span class="sxs-lookup"><span data-stu-id="42fe2-169">ISymUnmanagedWriter5 interface.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="42fe2-170">Sekcje pokrewne</span><span class="sxs-lookup"><span data-stu-id="42fe2-170">Related Sections</span></span>  
 [<span data-ttu-id="42fe2-171">Wyliczenia magazynu symboli diagnostycznych</span><span class="sxs-lookup"><span data-stu-id="42fe2-171">Diagnostics Symbol Store Enumerations</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/diagnostics-symbol-store-enumerations.md)  
  
 [<span data-ttu-id="42fe2-172">Struktury magazynu symboli diagnostycznych</span><span class="sxs-lookup"><span data-stu-id="42fe2-172">Diagnostics Symbol Store Structures</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/diagnostics-symbol-store-structures.md)  
  
 [<span data-ttu-id="42fe2-173">Debugowanie</span><span class="sxs-lookup"><span data-stu-id="42fe2-173">Debugging</span></span>](../../../../docs/framework/unmanaged-api/debugging/index.md)

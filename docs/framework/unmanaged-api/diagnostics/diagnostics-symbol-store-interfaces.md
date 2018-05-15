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
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="diagnostics-symbol-store-interfaces"></a><span data-ttu-id="d1be0-102">Interfejsy magazynu symboli diagnostycznych</span><span class="sxs-lookup"><span data-stu-id="d1be0-102">Diagnostics Symbol Store Interfaces</span></span>
<span data-ttu-id="d1be0-103">W tym temacie opisano niezarządzane interfejsy, umożliwiające kompilatora wygenerować informacje symbol do użycia przez debuger.</span><span class="sxs-lookup"><span data-stu-id="d1be0-103">This topic describes the unmanaged interfaces that enable a compiler to generate symbol information for use by a debugger.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="d1be0-104">W tej sekcji</span><span class="sxs-lookup"><span data-stu-id="d1be0-104">In This Section</span></span>  
 [<span data-ttu-id="d1be0-105">IBindingDisplay, interfejs</span><span class="sxs-lookup"><span data-stu-id="d1be0-105">IBindingDisplay Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/ibindingdisplay-interface.md)  
 <span data-ttu-id="d1be0-106">Udostępnia metody, które są wyświetlane bieżące informacje o powiązaniu o działającej aplikacji.</span><span class="sxs-lookup"><span data-stu-id="d1be0-106">Provides methods that display current binding information about the running application.</span></span>  
  
 [<span data-ttu-id="d1be0-107">IDebugAutoAttach, interfejs</span><span class="sxs-lookup"><span data-stu-id="d1be0-107">IDebugAutoAttach Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/idebugautoattach-interface.md)  
 <span data-ttu-id="d1be0-108">Definiuje interfejs dla dołączania automatycznie wywoływane serwera debugera.</span><span class="sxs-lookup"><span data-stu-id="d1be0-108">Defines the interface for a server-invoked debugger auto attach.</span></span>  
  
 [<span data-ttu-id="d1be0-109">INotifyConnection2, interfejs</span><span class="sxs-lookup"><span data-stu-id="d1be0-109">INotifyConnection2 Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/inotifyconnection2-interface.md)  
 <span data-ttu-id="d1be0-110">Deklaruje metody rejestrowanie i wyrejestrowywanie źródła powiadomień połączenia.</span><span class="sxs-lookup"><span data-stu-id="d1be0-110">Declares methods for registering and unregistering a connection notification source.</span></span>  
  
 [<span data-ttu-id="d1be0-111">INotifySink2, interfejs</span><span class="sxs-lookup"><span data-stu-id="d1be0-111">INotifySink2 Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/inotifysink2-interface.md)  
 <span data-ttu-id="d1be0-112">Deklaruje metody do odbioru powiadomienia.</span><span class="sxs-lookup"><span data-stu-id="d1be0-112">Declares methods for sink notification.</span></span>  
  
 [<span data-ttu-id="d1be0-113">INotifySource2, interfejs</span><span class="sxs-lookup"><span data-stu-id="d1be0-113">INotifySource2 Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/inotifysource2-interface.md)  
 <span data-ttu-id="d1be0-114">Deklaruje metody filtry powiadomień.</span><span class="sxs-lookup"><span data-stu-id="d1be0-114">Declares a method for setting notification filters.</span></span>  
  
 [<span data-ttu-id="d1be0-115">ISymENCUnmanagedMethod, interfejs</span><span class="sxs-lookup"><span data-stu-id="d1be0-115">ISymENCUnmanagedMethod Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymencunmanagedmethod-interface.md)  
 <span data-ttu-id="d1be0-116">Informacje dotyczące funkcji Edytuj i Kontynuuj.</span><span class="sxs-lookup"><span data-stu-id="d1be0-116">Provides information for the Edit and Continue feature.</span></span>  
  
 [<span data-ttu-id="d1be0-117">ISymUnmanagedAsyncMethod, interfejs</span><span class="sxs-lookup"><span data-stu-id="d1be0-117">ISymUnmanagedAsyncMethod Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedasyncmethod-interface.md)  
 <span data-ttu-id="d1be0-118">Ten interfejs jest uzupełnienie odczytu [isymunmanagedasyncmethodpropertieswriter — interfejs](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedasyncmethodpropertieswriter-interface.md).</span><span class="sxs-lookup"><span data-stu-id="d1be0-118">This interface is the reading complement to [ISymUnmanagedAsyncMethodPropertiesWriter Interface](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedasyncmethodpropertieswriter-interface.md).</span></span>  
  
 [<span data-ttu-id="d1be0-119">ISymUnmanagedAsyncMethodPropertiesWriter, interfejs</span><span class="sxs-lookup"><span data-stu-id="d1be0-119">ISymUnmanagedAsyncMethodPropertiesWriter Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedasyncmethodpropertieswriter-interface.md)  
 <span data-ttu-id="d1be0-120">Pozwala na określenie informacji o metodzie async opcjonalne na symbol — metoda.</span><span class="sxs-lookup"><span data-stu-id="d1be0-120">Allows definition of optional async method information per method symbol.</span></span> <span data-ttu-id="d1be0-121">Należy użyć z metodą otwarty (to znaczy między wywołań [OpenMethod — metoda](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-openmethod-method.md)i [CloseMethod — metoda](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-closemethod-method.md)).</span><span class="sxs-lookup"><span data-stu-id="d1be0-121">Must use with an opened method (that is, between calls to the [OpenMethod Method](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-openmethod-method.md)and the [CloseMethod Method](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-closemethod-method.md)).</span></span>  
  
 [<span data-ttu-id="d1be0-122">ISymUnmanagedBinder, interfejs</span><span class="sxs-lookup"><span data-stu-id="d1be0-122">ISymUnmanagedBinder Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedbinder-interface.md)  
 <span data-ttu-id="d1be0-123">Reprezentuje integrator symbol dla kodu niezarządzanego.</span><span class="sxs-lookup"><span data-stu-id="d1be0-123">Represents a symbol binder for unmanaged code.</span></span>  
  
 [<span data-ttu-id="d1be0-124">ISymUnmanagedBinder2, interfejs</span><span class="sxs-lookup"><span data-stu-id="d1be0-124">ISymUnmanagedBinder2 Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedbinder2-interface.md)  
 <span data-ttu-id="d1be0-125">Reprezentuje integrator symbol dla niezarządzanego kodu i rozszerza `ISymUnmanagedBinder` interfejsu.</span><span class="sxs-lookup"><span data-stu-id="d1be0-125">Represents a symbol binder for unmanaged code, and extends the `ISymUnmanagedBinder` interface.</span></span>  
  
 [<span data-ttu-id="d1be0-126">ISymUnmanagedBinder3, interfejs</span><span class="sxs-lookup"><span data-stu-id="d1be0-126">ISymUnmanagedBinder3 Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedbinder3-interface.md)  
 <span data-ttu-id="d1be0-127">Reprezentuje integrator symbol dla niezarządzanego kodu i rozszerza `ISymUnmanagedBinder` interfejsu.</span><span class="sxs-lookup"><span data-stu-id="d1be0-127">Represents a symbol binder for unmanaged code, and extends the `ISymUnmanagedBinder` interface.</span></span>  
  
 [<span data-ttu-id="d1be0-128">ISymUnmanagedConstant, interfejs</span><span class="sxs-lookup"><span data-stu-id="d1be0-128">ISymUnmanagedConstant Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedconstant-interface.md)  
 <span data-ttu-id="d1be0-129">Zapewnia dostęp do niezarządzanego stałe.</span><span class="sxs-lookup"><span data-stu-id="d1be0-129">Provides access to unmanaged constants.</span></span>  
  
 [<span data-ttu-id="d1be0-130">ISymUnmanagedDispose, interfejs</span><span class="sxs-lookup"><span data-stu-id="d1be0-130">ISymUnmanagedDispose Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanageddispose-interface.md)  
 <span data-ttu-id="d1be0-131">Usuwa zasoby niezarządzane.</span><span class="sxs-lookup"><span data-stu-id="d1be0-131">Disposes of unmanaged resources.</span></span>  
  
 [<span data-ttu-id="d1be0-132">ISymUnmanagedDocument, interfejs</span><span class="sxs-lookup"><span data-stu-id="d1be0-132">ISymUnmanagedDocument Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanageddocument-interface.md)  
 <span data-ttu-id="d1be0-133">Reprezentuje dokument odwołuje się magazynu symboli.</span><span class="sxs-lookup"><span data-stu-id="d1be0-133">Represents a document referenced by a symbol store.</span></span>  
  
 [<span data-ttu-id="d1be0-134">ISymUnmanagedDocumentWriter, interfejs</span><span class="sxs-lookup"><span data-stu-id="d1be0-134">ISymUnmanagedDocumentWriter Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanageddocumentwriter-interface.md)  
 <span data-ttu-id="d1be0-135">Udostępnia metody do zapisywania dokumentu odwołuje się magazynu symboli.</span><span class="sxs-lookup"><span data-stu-id="d1be0-135">Provides methods for writing to a document referenced by a symbol store.</span></span>  
  
 [<span data-ttu-id="d1be0-136">ISymUnmanagedENCUpdate, interfejs</span><span class="sxs-lookup"><span data-stu-id="d1be0-136">ISymUnmanagedENCUpdate Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedencupdate-interface.md)  
 <span data-ttu-id="d1be0-137">Udostępnia metody dla funkcji Edytuj i Kontynuuj.</span><span class="sxs-lookup"><span data-stu-id="d1be0-137">Provides methods for the Edit and Continue feature.</span></span>  
  
 [<span data-ttu-id="d1be0-138">ISymUnmanagedMethod, interfejs</span><span class="sxs-lookup"><span data-stu-id="d1be0-138">ISymUnmanagedMethod Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedmethod-interface.md)  
 <span data-ttu-id="d1be0-139">Reprezentuje metodę w magazynie symboli.</span><span class="sxs-lookup"><span data-stu-id="d1be0-139">Represents a method within the symbol store.</span></span>  
  
 [<span data-ttu-id="d1be0-140">ISymUnmanagedNamespace, interfejs</span><span class="sxs-lookup"><span data-stu-id="d1be0-140">ISymUnmanagedNamespace Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagednamespace-interface.md)  
 <span data-ttu-id="d1be0-141">Reprezentuje przestrzeni nazw.</span><span class="sxs-lookup"><span data-stu-id="d1be0-141">Represents a namespace.</span></span>  
  
 [<span data-ttu-id="d1be0-142">ISymUnmanagedReader, interfejs</span><span class="sxs-lookup"><span data-stu-id="d1be0-142">ISymUnmanagedReader Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedreader-interface.md)  
 <span data-ttu-id="d1be0-143">Reprezentuje czytnika symboli, która zapewnia dostęp do dokumentów, metod i zmiennych w magazynie symboli.</span><span class="sxs-lookup"><span data-stu-id="d1be0-143">Represents a symbol reader that provides access to documents, methods, and variables within a symbol store.</span></span>  
  
 [<span data-ttu-id="d1be0-144">ISymUnmanagedReader2, interfejs</span><span class="sxs-lookup"><span data-stu-id="d1be0-144">ISymUnmanagedReader2 Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedreader2-interface.md)  
 <span data-ttu-id="d1be0-145">Pobiera metodę czytnika symboli podany token metody i numer wersji edycji i kopii.</span><span class="sxs-lookup"><span data-stu-id="d1be0-145">Gets a symbol reader method given a method token and an edit-and-copy version number.</span></span>  
  
 [<span data-ttu-id="d1be0-146">ISymUnmanagedReaderSymbolSearchInfo, interfejs</span><span class="sxs-lookup"><span data-stu-id="d1be0-146">ISymUnmanagedReaderSymbolSearchInfo Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedreadersymbolsearchinfo-interface.md)  
 <span data-ttu-id="d1be0-147">Udostępnia metody, które zawierają informacje o wyszukiwaniu symboli.</span><span class="sxs-lookup"><span data-stu-id="d1be0-147">Provides methods that get symbol search information.</span></span>  
  
 [<span data-ttu-id="d1be0-148">ISymUnmanagedScope, interfejs</span><span class="sxs-lookup"><span data-stu-id="d1be0-148">ISymUnmanagedScope Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedscope-interface.md)  
 <span data-ttu-id="d1be0-149">Reprezentuje leksykalne zakresu w metodzie.</span><span class="sxs-lookup"><span data-stu-id="d1be0-149">Represents a lexical scope within a method.</span></span>  
  
 [<span data-ttu-id="d1be0-150">ISymUnmanagedScope2, interfejs</span><span class="sxs-lookup"><span data-stu-id="d1be0-150">ISymUnmanagedScope2 Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedscope2-interface.md)  
 <span data-ttu-id="d1be0-151">Reprezentuje leksykalne zakresu w metodzie i rozszerza `ISymUnmanagedScope` interfejs za pomocą metody pobierające informacje o stałych zdefiniowana w zakresie.</span><span class="sxs-lookup"><span data-stu-id="d1be0-151">Represents a lexical scope within a method, and extends the `ISymUnmanagedScope` interface with methods that get information about constants defined within the scope..</span></span>  
  
 [<span data-ttu-id="d1be0-152">ISymUnmanagedSourceServerModule, interfejs</span><span class="sxs-lookup"><span data-stu-id="d1be0-152">ISymUnmanagedSourceServerModule Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedsourceservermodule-interface.md)  
 <span data-ttu-id="d1be0-153">Udostępnia dane z serwera źródłowego dla modułu.</span><span class="sxs-lookup"><span data-stu-id="d1be0-153">Provides source server data for a module.</span></span>  
  
 [<span data-ttu-id="d1be0-154">ISymUnmanagedSymbolSearchInfo, interfejs</span><span class="sxs-lookup"><span data-stu-id="d1be0-154">ISymUnmanagedSymbolSearchInfo Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedsymbolsearchinfo-interface.md)  
 <span data-ttu-id="d1be0-155">Udostępnia metody, które zawierają informacje o ścieżce wyszukiwania.</span><span class="sxs-lookup"><span data-stu-id="d1be0-155">Provides methods that get information about the search path.</span></span>  
  
 [<span data-ttu-id="d1be0-156">ISymUnmanagedVariable, interfejs</span><span class="sxs-lookup"><span data-stu-id="d1be0-156">ISymUnmanagedVariable Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedvariable-interface.md)  
 <span data-ttu-id="d1be0-157">Reprezentuje zmienną, np. parametr, lokalnej zmiennej lub pola.</span><span class="sxs-lookup"><span data-stu-id="d1be0-157">Represents a variable, such as a parameter, a local variable, or a field.</span></span>  
  
 [<span data-ttu-id="d1be0-158">ISymUnmanagedWriter, interfejs</span><span class="sxs-lookup"><span data-stu-id="d1be0-158">ISymUnmanagedWriter Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-interface.md)  
 <span data-ttu-id="d1be0-159">Reprezentuje edytor symboli i udostępnia metody, aby zdefiniować dokumenty, punkty sekwencji leksykalne zakresy i zmienne.</span><span class="sxs-lookup"><span data-stu-id="d1be0-159">Represents a symbol writer, and provides methods to define documents, sequence points, lexical scopes, and variables.</span></span>  
  
 [<span data-ttu-id="d1be0-160">ISymUnmanagedWriter2, interfejs</span><span class="sxs-lookup"><span data-stu-id="d1be0-160">ISymUnmanagedWriter2 Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter2-interface.md)  
 <span data-ttu-id="d1be0-161">Reprezentuje edytor symboli i udostępnia metody, aby zdefiniować dokumenty, punkty sekwencji leksykalne zakresy i zmienne.</span><span class="sxs-lookup"><span data-stu-id="d1be0-161">Represents a symbol writer, and provides methods to define documents, sequence points, lexical scopes, and variables.</span></span> <span data-ttu-id="d1be0-162">Rozszerza `ISymUnmanagedWriter` interfejsu.</span><span class="sxs-lookup"><span data-stu-id="d1be0-162">Extends the `ISymUnmanagedWriter` interface.</span></span>  
  
 [<span data-ttu-id="d1be0-163">ISymUnmanagedWriter3, interfejs</span><span class="sxs-lookup"><span data-stu-id="d1be0-163">ISymUnmanagedWriter3 Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter3-interface.md)  
 <span data-ttu-id="d1be0-164">Reprezentuje edytor symboli i udostępnia metody, aby zdefiniować dokumenty, punkty sekwencji leksykalne zakresy i zmienne.</span><span class="sxs-lookup"><span data-stu-id="d1be0-164">Represents a symbol writer, and provides methods to define documents, sequence points, lexical scopes, and variables.</span></span> <span data-ttu-id="d1be0-165">Rozszerza `ISymUnmanagedWriter` interfejsu.</span><span class="sxs-lookup"><span data-stu-id="d1be0-165">Extends the `ISymUnmanagedWriter` interface.</span></span>  
  
 [<span data-ttu-id="d1be0-166">ISymUnmanagedWriter4, interfejs</span><span class="sxs-lookup"><span data-stu-id="d1be0-166">ISymUnmanagedWriter4 Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter4-interface.md)  
 <span data-ttu-id="d1be0-167">Isymunmanagedwriter4 — interfejs.</span><span class="sxs-lookup"><span data-stu-id="d1be0-167">ISymUnmanagedWriter4 interface.</span></span>  
  
 [<span data-ttu-id="d1be0-168">ISymUnmanagedWriter5, interfejs</span><span class="sxs-lookup"><span data-stu-id="d1be0-168">ISymUnmanagedWriter5 Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter5-interface.md)  
 <span data-ttu-id="d1be0-169">Isymunmanagedwriter5 — interfejs.</span><span class="sxs-lookup"><span data-stu-id="d1be0-169">ISymUnmanagedWriter5 interface.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="d1be0-170">Sekcje pokrewne</span><span class="sxs-lookup"><span data-stu-id="d1be0-170">Related Sections</span></span>  
 [<span data-ttu-id="d1be0-171">Wyliczenia magazynu symboli diagnostycznych</span><span class="sxs-lookup"><span data-stu-id="d1be0-171">Diagnostics Symbol Store Enumerations</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/diagnostics-symbol-store-enumerations.md)  
  
 [<span data-ttu-id="d1be0-172">Struktury magazynu symboli diagnostycznych</span><span class="sxs-lookup"><span data-stu-id="d1be0-172">Diagnostics Symbol Store Structures</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/diagnostics-symbol-store-structures.md)  
  
 [<span data-ttu-id="d1be0-173">Debugowanie</span><span class="sxs-lookup"><span data-stu-id="d1be0-173">Debugging</span></span>](../../../../docs/framework/unmanaged-api/debugging/index.md)

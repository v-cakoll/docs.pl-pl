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
ms.openlocfilehash: bdb691570a9a2bf7bd2bb21af500b06c10b0bc53
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/23/2019
ms.locfileid: "74448524"
---
# <a name="diagnostics-symbol-store-interfaces"></a><span data-ttu-id="7927e-102">Interfejsy magazynu symboli diagnostycznych</span><span class="sxs-lookup"><span data-stu-id="7927e-102">Diagnostics Symbol Store Interfaces</span></span>
<span data-ttu-id="7927e-103">W tym temacie opisano niezarządzane interfejsy, które umożliwiają kompilatorowi generowanie informacji o symbolach do użycia przez debuger.</span><span class="sxs-lookup"><span data-stu-id="7927e-103">This topic describes the unmanaged interfaces that enable a compiler to generate symbol information for use by a debugger.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="7927e-104">W tej sekcji</span><span class="sxs-lookup"><span data-stu-id="7927e-104">In This Section</span></span>  
 [<span data-ttu-id="7927e-105">IBindingDisplay, interfejs</span><span class="sxs-lookup"><span data-stu-id="7927e-105">IBindingDisplay Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/ibindingdisplay-interface.md)  
 <span data-ttu-id="7927e-106">Dostarcza metody, które wyświetlają bieżące informacje o powiązaniu dla działającej aplikacji.</span><span class="sxs-lookup"><span data-stu-id="7927e-106">Provides methods that display current binding information about the running application.</span></span>  
  
 [<span data-ttu-id="7927e-107">IDebugAutoAttach, interfejs</span><span class="sxs-lookup"><span data-stu-id="7927e-107">IDebugAutoAttach Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/idebugautoattach-interface.md)  
 <span data-ttu-id="7927e-108">Definiuje interfejs dla automatycznie dołączanego debugera dla serwera.</span><span class="sxs-lookup"><span data-stu-id="7927e-108">Defines the interface for a server-invoked debugger auto attach.</span></span>  
  
 [<span data-ttu-id="7927e-109">INotifyConnection2, interfejs</span><span class="sxs-lookup"><span data-stu-id="7927e-109">INotifyConnection2 Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/inotifyconnection2-interface.md)  
 <span data-ttu-id="7927e-110">Deklaruje metody rejestrowania źródła powiadomień połączenia i wyrejestrowywania go.</span><span class="sxs-lookup"><span data-stu-id="7927e-110">Declares methods for registering and unregistering a connection notification source.</span></span>  
  
 [<span data-ttu-id="7927e-111">INotifySink2, interfejs</span><span class="sxs-lookup"><span data-stu-id="7927e-111">INotifySink2 Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/inotifysink2-interface.md)  
 <span data-ttu-id="7927e-112">Deklaruje metody powiadamiania o ujściach.</span><span class="sxs-lookup"><span data-stu-id="7927e-112">Declares methods for sink notification.</span></span>  
  
 [<span data-ttu-id="7927e-113">INotifySource2, interfejs</span><span class="sxs-lookup"><span data-stu-id="7927e-113">INotifySource2 Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/inotifysource2-interface.md)  
 <span data-ttu-id="7927e-114">Deklaruje metodę ustawiania filtrów powiadomień.</span><span class="sxs-lookup"><span data-stu-id="7927e-114">Declares a method for setting notification filters.</span></span>  
  
 [<span data-ttu-id="7927e-115">ISymENCUnmanagedMethod, interfejs</span><span class="sxs-lookup"><span data-stu-id="7927e-115">ISymENCUnmanagedMethod Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymencunmanagedmethod-interface.md)  
 <span data-ttu-id="7927e-116">Zawiera informacje dotyczące funkcji Edytuj i Kontynuuj.</span><span class="sxs-lookup"><span data-stu-id="7927e-116">Provides information for the Edit and Continue feature.</span></span>  
  
 [<span data-ttu-id="7927e-117">ISymUnmanagedAsyncMethod, interfejs</span><span class="sxs-lookup"><span data-stu-id="7927e-117">ISymUnmanagedAsyncMethod Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedasyncmethod-interface.md)  
 <span data-ttu-id="7927e-118">Ten interfejs jest uzupełnieniem odczytu do [interfejsu ISymUnmanagedAsyncMethodPropertiesWriter](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedasyncmethodpropertieswriter-interface.md).</span><span class="sxs-lookup"><span data-stu-id="7927e-118">This interface is the reading complement to [ISymUnmanagedAsyncMethodPropertiesWriter Interface](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedasyncmethodpropertieswriter-interface.md).</span></span>  
  
 [<span data-ttu-id="7927e-119">ISymUnmanagedAsyncMethodPropertiesWriter, interfejs</span><span class="sxs-lookup"><span data-stu-id="7927e-119">ISymUnmanagedAsyncMethodPropertiesWriter Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedasyncmethodpropertieswriter-interface.md)  
 <span data-ttu-id="7927e-120">Zezwala na definiowanie opcjonalnych informacji o metodzie asynchronicznej dla symbolu metody.</span><span class="sxs-lookup"><span data-stu-id="7927e-120">Allows definition of optional async method information per method symbol.</span></span> <span data-ttu-id="7927e-121">Musi być używana z otwartą metodą (czyli między wywołaniami [metody OpenMethod —](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-openmethod-method.md)i [CloseMethod —](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-closemethod-method.md)).</span><span class="sxs-lookup"><span data-stu-id="7927e-121">Must use with an opened method (that is, between calls to the [OpenMethod Method](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-openmethod-method.md)and the [CloseMethod Method](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-closemethod-method.md)).</span></span>  
  
 [<span data-ttu-id="7927e-122">ISymUnmanagedBinder, interfejs</span><span class="sxs-lookup"><span data-stu-id="7927e-122">ISymUnmanagedBinder Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedbinder-interface.md)  
 <span data-ttu-id="7927e-123">Reprezentuje spinacz symboliczny dla niezarządzanego kodu.</span><span class="sxs-lookup"><span data-stu-id="7927e-123">Represents a symbol binder for unmanaged code.</span></span>  
  
 [<span data-ttu-id="7927e-124">ISymUnmanagedBinder2, interfejs</span><span class="sxs-lookup"><span data-stu-id="7927e-124">ISymUnmanagedBinder2 Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedbinder2-interface.md)  
 <span data-ttu-id="7927e-125">Reprezentuje spinacz symboliczny dla kodu niezarządzanego i rozszerza interfejs `ISymUnmanagedBinder`.</span><span class="sxs-lookup"><span data-stu-id="7927e-125">Represents a symbol binder for unmanaged code, and extends the `ISymUnmanagedBinder` interface.</span></span>  
  
 [<span data-ttu-id="7927e-126">ISymUnmanagedBinder3, interfejs</span><span class="sxs-lookup"><span data-stu-id="7927e-126">ISymUnmanagedBinder3 Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedbinder3-interface.md)  
 <span data-ttu-id="7927e-127">Reprezentuje spinacz symboliczny dla kodu niezarządzanego i rozszerza interfejs `ISymUnmanagedBinder`.</span><span class="sxs-lookup"><span data-stu-id="7927e-127">Represents a symbol binder for unmanaged code, and extends the `ISymUnmanagedBinder` interface.</span></span>  
  
 [<span data-ttu-id="7927e-128">ISymUnmanagedConstant, interfejs</span><span class="sxs-lookup"><span data-stu-id="7927e-128">ISymUnmanagedConstant Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedconstant-interface.md)  
 <span data-ttu-id="7927e-129">Zapewnia dostęp do stałych niezarządzanych.</span><span class="sxs-lookup"><span data-stu-id="7927e-129">Provides access to unmanaged constants.</span></span>  
  
 [<span data-ttu-id="7927e-130">ISymUnmanagedDispose, interfejs</span><span class="sxs-lookup"><span data-stu-id="7927e-130">ISymUnmanagedDispose Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanageddispose-interface.md)  
 <span data-ttu-id="7927e-131">Usuwa niezarządzane zasoby.</span><span class="sxs-lookup"><span data-stu-id="7927e-131">Disposes of unmanaged resources.</span></span>  
  
 [<span data-ttu-id="7927e-132">ISymUnmanagedDocument, interfejs</span><span class="sxs-lookup"><span data-stu-id="7927e-132">ISymUnmanagedDocument Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanageddocument-interface.md)  
 <span data-ttu-id="7927e-133">Reprezentuje dokument, do którego odwołuje się magazyn symboli.</span><span class="sxs-lookup"><span data-stu-id="7927e-133">Represents a document referenced by a symbol store.</span></span>  
  
 [<span data-ttu-id="7927e-134">ISymUnmanagedDocumentWriter, interfejs</span><span class="sxs-lookup"><span data-stu-id="7927e-134">ISymUnmanagedDocumentWriter Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanageddocumentwriter-interface.md)  
 <span data-ttu-id="7927e-135">Zapewnia metody zapisu do dokumentu, do którego odwołuje się magazyn symboli.</span><span class="sxs-lookup"><span data-stu-id="7927e-135">Provides methods for writing to a document referenced by a symbol store.</span></span>  
  
 [<span data-ttu-id="7927e-136">ISymUnmanagedENCUpdate, interfejs</span><span class="sxs-lookup"><span data-stu-id="7927e-136">ISymUnmanagedENCUpdate Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedencupdate-interface.md)  
 <span data-ttu-id="7927e-137">Zapewnia metody funkcji Edytuj i Kontynuuj.</span><span class="sxs-lookup"><span data-stu-id="7927e-137">Provides methods for the Edit and Continue feature.</span></span>  
  
 [<span data-ttu-id="7927e-138">ISymUnmanagedMethod, interfejs</span><span class="sxs-lookup"><span data-stu-id="7927e-138">ISymUnmanagedMethod Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedmethod-interface.md)  
 <span data-ttu-id="7927e-139">Reprezentuje metodę w magazynie symboli.</span><span class="sxs-lookup"><span data-stu-id="7927e-139">Represents a method within the symbol store.</span></span>  
  
 [<span data-ttu-id="7927e-140">ISymUnmanagedNamespace, interfejs</span><span class="sxs-lookup"><span data-stu-id="7927e-140">ISymUnmanagedNamespace Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagednamespace-interface.md)  
 <span data-ttu-id="7927e-141">Reprezentuje przestrzeń nazw.</span><span class="sxs-lookup"><span data-stu-id="7927e-141">Represents a namespace.</span></span>  
  
 [<span data-ttu-id="7927e-142">ISymUnmanagedReader, interfejs</span><span class="sxs-lookup"><span data-stu-id="7927e-142">ISymUnmanagedReader Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedreader-interface.md)  
 <span data-ttu-id="7927e-143">Reprezentuje czytnik symboli, który zapewnia dostęp do dokumentów, metod i zmiennych w magazynie symboli.</span><span class="sxs-lookup"><span data-stu-id="7927e-143">Represents a symbol reader that provides access to documents, methods, and variables within a symbol store.</span></span>  
  
 [<span data-ttu-id="7927e-144">ISymUnmanagedReader2, interfejs</span><span class="sxs-lookup"><span data-stu-id="7927e-144">ISymUnmanagedReader2 Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedreader2-interface.md)  
 <span data-ttu-id="7927e-145">Pobiera metodę czytnika symboli, używając tokenu metody oraz numeru wersji Edit-and-Copy.</span><span class="sxs-lookup"><span data-stu-id="7927e-145">Gets a symbol reader method given a method token and an edit-and-copy version number.</span></span>  
  
 [<span data-ttu-id="7927e-146">ISymUnmanagedReaderSymbolSearchInfo, interfejs</span><span class="sxs-lookup"><span data-stu-id="7927e-146">ISymUnmanagedReaderSymbolSearchInfo Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedreadersymbolsearchinfo-interface.md)  
 <span data-ttu-id="7927e-147">Dostarcza metody, które pobierają informacje o wyszukiwaniu symboli.</span><span class="sxs-lookup"><span data-stu-id="7927e-147">Provides methods that get symbol search information.</span></span>  
  
 [<span data-ttu-id="7927e-148">ISymUnmanagedScope, interfejs</span><span class="sxs-lookup"><span data-stu-id="7927e-148">ISymUnmanagedScope Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedscope-interface.md)  
 <span data-ttu-id="7927e-149">Reprezentuje zakres leksykalny w ramach metody.</span><span class="sxs-lookup"><span data-stu-id="7927e-149">Represents a lexical scope within a method.</span></span>  
  
 [<span data-ttu-id="7927e-150">ISymUnmanagedScope2, interfejs</span><span class="sxs-lookup"><span data-stu-id="7927e-150">ISymUnmanagedScope2 Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedscope2-interface.md)  
 <span data-ttu-id="7927e-151">Reprezentuje zakres leksykalny w ramach metody i rozszerza interfejs `ISymUnmanagedScope` przy użyciu metod, które pobierają informacje o stałych zdefiniowanych w zakresie.</span><span class="sxs-lookup"><span data-stu-id="7927e-151">Represents a lexical scope within a method, and extends the `ISymUnmanagedScope` interface with methods that get information about constants defined within the scope..</span></span>  
  
 [<span data-ttu-id="7927e-152">ISymUnmanagedSourceServerModule, interfejs</span><span class="sxs-lookup"><span data-stu-id="7927e-152">ISymUnmanagedSourceServerModule Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedsourceservermodule-interface.md)  
 <span data-ttu-id="7927e-153">Zapewnia dane serwera źródłowego dla modułu.</span><span class="sxs-lookup"><span data-stu-id="7927e-153">Provides source server data for a module.</span></span>  
  
 [<span data-ttu-id="7927e-154">ISymUnmanagedSymbolSearchInfo, interfejs</span><span class="sxs-lookup"><span data-stu-id="7927e-154">ISymUnmanagedSymbolSearchInfo Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedsymbolsearchinfo-interface.md)  
 <span data-ttu-id="7927e-155">Dostarcza metody, które pobierają informacje o ścieżce wyszukiwania.</span><span class="sxs-lookup"><span data-stu-id="7927e-155">Provides methods that get information about the search path.</span></span>  
  
 [<span data-ttu-id="7927e-156">ISymUnmanagedVariable, interfejs</span><span class="sxs-lookup"><span data-stu-id="7927e-156">ISymUnmanagedVariable Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedvariable-interface.md)  
 <span data-ttu-id="7927e-157">Reprezentuje zmienną, taką jak parametr, zmienna lokalna lub pole.</span><span class="sxs-lookup"><span data-stu-id="7927e-157">Represents a variable, such as a parameter, a local variable, or a field.</span></span>  
  
 [<span data-ttu-id="7927e-158">ISymUnmanagedWriter, interfejs</span><span class="sxs-lookup"><span data-stu-id="7927e-158">ISymUnmanagedWriter Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-interface.md)  
 <span data-ttu-id="7927e-159">Reprezentuje moduł zapisujący symboli i zawiera metody definiowania dokumentów, punktów sekwencji, zakresów leksykalnych i zmiennych.</span><span class="sxs-lookup"><span data-stu-id="7927e-159">Represents a symbol writer, and provides methods to define documents, sequence points, lexical scopes, and variables.</span></span>  
  
 [<span data-ttu-id="7927e-160">ISymUnmanagedWriter2, interfejs</span><span class="sxs-lookup"><span data-stu-id="7927e-160">ISymUnmanagedWriter2 Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter2-interface.md)  
 <span data-ttu-id="7927e-161">Reprezentuje moduł zapisujący symboli i zawiera metody definiowania dokumentów, punktów sekwencji, zakresów leksykalnych i zmiennych.</span><span class="sxs-lookup"><span data-stu-id="7927e-161">Represents a symbol writer, and provides methods to define documents, sequence points, lexical scopes, and variables.</span></span> <span data-ttu-id="7927e-162">Rozszerza interfejs `ISymUnmanagedWriter`.</span><span class="sxs-lookup"><span data-stu-id="7927e-162">Extends the `ISymUnmanagedWriter` interface.</span></span>  
  
 [<span data-ttu-id="7927e-163">ISymUnmanagedWriter3, interfejs</span><span class="sxs-lookup"><span data-stu-id="7927e-163">ISymUnmanagedWriter3 Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter3-interface.md)  
 <span data-ttu-id="7927e-164">Reprezentuje moduł zapisujący symboli i zawiera metody definiowania dokumentów, punktów sekwencji, zakresów leksykalnych i zmiennych.</span><span class="sxs-lookup"><span data-stu-id="7927e-164">Represents a symbol writer, and provides methods to define documents, sequence points, lexical scopes, and variables.</span></span> <span data-ttu-id="7927e-165">Rozszerza interfejs `ISymUnmanagedWriter`.</span><span class="sxs-lookup"><span data-stu-id="7927e-165">Extends the `ISymUnmanagedWriter` interface.</span></span>  
  
 [<span data-ttu-id="7927e-166">ISymUnmanagedWriter4, interfejs</span><span class="sxs-lookup"><span data-stu-id="7927e-166">ISymUnmanagedWriter4 Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter4-interface.md)  
 <span data-ttu-id="7927e-167">Interfejs ISymUnmanagedWriter4.</span><span class="sxs-lookup"><span data-stu-id="7927e-167">ISymUnmanagedWriter4 interface.</span></span>  
  
 [<span data-ttu-id="7927e-168">ISymUnmanagedWriter5, interfejs</span><span class="sxs-lookup"><span data-stu-id="7927e-168">ISymUnmanagedWriter5 Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter5-interface.md)  
 <span data-ttu-id="7927e-169">Interfejs ISymUnmanagedWriter5.</span><span class="sxs-lookup"><span data-stu-id="7927e-169">ISymUnmanagedWriter5 interface.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="7927e-170">Sekcje pokrewne</span><span class="sxs-lookup"><span data-stu-id="7927e-170">Related Sections</span></span>  
 [<span data-ttu-id="7927e-171">Wyliczenia magazynu symboli diagnostycznych</span><span class="sxs-lookup"><span data-stu-id="7927e-171">Diagnostics Symbol Store Enumerations</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/diagnostics-symbol-store-enumerations.md)  
  
 [<span data-ttu-id="7927e-172">Struktury magazynu symboli diagnostycznych</span><span class="sxs-lookup"><span data-stu-id="7927e-172">Diagnostics Symbol Store Structures</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/diagnostics-symbol-store-structures.md)  
  
 [<span data-ttu-id="7927e-173">Debugowanie</span><span class="sxs-lookup"><span data-stu-id="7927e-173">Debugging</span></span>](../../../../docs/framework/unmanaged-api/debugging/index.md)

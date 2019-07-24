---
title: Mgmtclassgen.exe (Zarządzanie generatorem silnie typizowanej klasy)
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- CIM types
- Management Strongly Typed Class Generator
- WMI class
- Mgmtclassgen.exe
- early-bound managed classes
ms.assetid: 02ce6699-49b5-4a0b-b0d5-1003c491232e
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 60f48422d23fc5db743eeb05e3eddeb732bff102
ms.sourcegitcommit: 30a83efb57c468da74e9e218de26cf88d3254597
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/20/2019
ms.locfileid: "68364023"
---
# <a name="mgmtclassgenexe-management-strongly-typed-class-generator"></a><span data-ttu-id="c163d-102">Mgmtclassgen.exe (Zarządzanie generatorem silnie typizowanej klasy)</span><span class="sxs-lookup"><span data-stu-id="c163d-102">Mgmtclassgen.exe (Management Strongly Typed Class Generator)</span></span>
<span data-ttu-id="c163d-103">Narzędzie Management Strongly Typed Class Generator umożliwia szybkie generowanie wcześnie powiązanych klas zarządzanych dla określonej klasy Instrumentacji zarządzania Windows (WMI).</span><span class="sxs-lookup"><span data-stu-id="c163d-103">The Management Strongly Typed Class Generator tool enables you to quickly generate an early-bound managed class for a specified Windows Management Instrumentation (WMI) class.</span></span> <span data-ttu-id="c163d-104">Wygenerowana klasa upraszcza kod, który trzeba napisać, aby uzyskać dostęp do wystąpienia klasy WMI.</span><span class="sxs-lookup"><span data-stu-id="c163d-104">The generated class simplifies the code you must write to access an instance of the WMI class.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c163d-105">Składnia</span><span class="sxs-lookup"><span data-stu-id="c163d-105">Syntax</span></span>  
  
```  
mgmtclassgen   
WMIClass [options]   
```  
  
|<span data-ttu-id="c163d-106">Argument</span><span class="sxs-lookup"><span data-stu-id="c163d-106">Argument</span></span>|<span data-ttu-id="c163d-107">Opis</span><span class="sxs-lookup"><span data-stu-id="c163d-107">Description</span></span>|  
|--------------|-----------------|  
|<span data-ttu-id="c163d-108">*WMIClass*</span><span class="sxs-lookup"><span data-stu-id="c163d-108">*WMIClass*</span></span>|<span data-ttu-id="c163d-109">Klasa Instrumentacji zarządzania Windows, dla której jest generowana wcześnie powiązana klasa zarządzana.</span><span class="sxs-lookup"><span data-stu-id="c163d-109">The Windows Management Instrumentation class for which to generate an early-bound managed class.</span></span>|  
  
|<span data-ttu-id="c163d-110">Opcja</span><span class="sxs-lookup"><span data-stu-id="c163d-110">Option</span></span>|<span data-ttu-id="c163d-111">Opis</span><span class="sxs-lookup"><span data-stu-id="c163d-111">Description</span></span>|  
|------------|-----------------|  
|<span data-ttu-id="c163d-112">**/l** *języka*</span><span class="sxs-lookup"><span data-stu-id="c163d-112">**/l**  *language*</span></span>|<span data-ttu-id="c163d-113">Określa język, w którym ma zostać wygenerowana wcześnie powiązana klasa zarządzana.</span><span class="sxs-lookup"><span data-stu-id="c163d-113">Specifies the language in which to generate the early-bound managed class.</span></span> <span data-ttu-id="c163d-114">Jako argumentu języka  można określićC#cs (; default), **VB** (Visual Basic),C++ **MC** () lub **js** (JScript).</span><span class="sxs-lookup"><span data-stu-id="c163d-114">You can specify **CS** (C#; default), **VB** (Visual Basic),  **MC** (C++), or **JS** (JScript) as the language argument.</span></span>|  
|<span data-ttu-id="c163d-115">**/m** *maszyny*</span><span class="sxs-lookup"><span data-stu-id="c163d-115">**/m**  *machine*</span></span>|<span data-ttu-id="c163d-116">Określa komputer, z którym należy nawiązać połączenie (na tym komputerze znajduje się klasa WMI).</span><span class="sxs-lookup"><span data-stu-id="c163d-116">Specifies the computer to connect to, where the WMI class resides.</span></span> <span data-ttu-id="c163d-117">Wartością domyślną jest komputer lokalny.</span><span class="sxs-lookup"><span data-stu-id="c163d-117">The default is the local computer.</span></span>|  
|<span data-ttu-id="c163d-118">**/n** *ścieżki*</span><span class="sxs-lookup"><span data-stu-id="c163d-118">**/n**  *path*</span></span>|<span data-ttu-id="c163d-119">Określa ścieżkę do przestrzeni nazw usługi WMI zawierającej odpowiednią klasę WMI.</span><span class="sxs-lookup"><span data-stu-id="c163d-119">Specifies the path to the WMI namespace that contains the WMI class.</span></span> <span data-ttu-id="c163d-120">Jeśli ta opcja nie zostanie określona, narzędzie generuje kod dla *WMIClass* w domyślnej przestrzeni nazw **root\cimv2** .</span><span class="sxs-lookup"><span data-stu-id="c163d-120">If you do not specify this option, the tool generates code for *WMIClass* in the default **Root\cimv2** namespace.</span></span>|  
|<span data-ttu-id="c163d-121">**/o** *classnamespace*</span><span class="sxs-lookup"><span data-stu-id="c163d-121">**/o**  *classnamespace*</span></span>|<span data-ttu-id="c163d-122">Określa przestrzeń nazw platformy .NET, w której ma zostać wygenerowana klasa kodu zarządzanego.</span><span class="sxs-lookup"><span data-stu-id="c163d-122">Specifies the .NET namespace in which to generate the managed code class.</span></span> <span data-ttu-id="c163d-123">Jeśli ta opcja nie zostanie określona, narzędzie wygeneruje przestrzeń nazw, używając przestrzeni nazw usługi WMI i prefiksu schematu.</span><span class="sxs-lookup"><span data-stu-id="c163d-123">If you do not specify this option, the tool generates the namespace using the WMI namespace and the schema prefix.</span></span> <span data-ttu-id="c163d-124">Prefiks schematu jest częścią nazwy klasy poprzedzającą znak podkreślenia.</span><span class="sxs-lookup"><span data-stu-id="c163d-124">The schema prefix is the part of the class name preceding the underscore character.</span></span> <span data-ttu-id="c163d-125">Na przykład dla klasy **Win32_OperatingSystem** w przestrzeni nazw **root\cimv2** narzędzie wygeneruje klasę w **katalogu głównym. CIMV2. Win32**.</span><span class="sxs-lookup"><span data-stu-id="c163d-125">For example, for the **Win32_OperatingSystem** class in the **Root\cimv2** namespace, the tool would generate the class in **ROOT.CIMV2.Win32**.</span></span>|  
|<span data-ttu-id="c163d-126">**/p** *filepath*</span><span class="sxs-lookup"><span data-stu-id="c163d-126">**/p**  *filepath*</span></span>|<span data-ttu-id="c163d-127">Określa ścieżkę do pliku, w którym ma zostać zapisany wygenerowany kod.</span><span class="sxs-lookup"><span data-stu-id="c163d-127">Specifies the path to the file in which to save the generated code.</span></span> <span data-ttu-id="c163d-128">Jeśli ta opcja nie zostanie określona, narzędzie utworzy plik w bieżącym katalogu.</span><span class="sxs-lookup"><span data-stu-id="c163d-128">If you do not specify this option, the tool creates the file in the current directory.</span></span> <span data-ttu-id="c163d-129">Nazwa klasy i pliku, w którym generuje klasę przy użyciu argumentu *WMIClass* .</span><span class="sxs-lookup"><span data-stu-id="c163d-129">It names the class and file in which it generates the class using the *WMIClass* argument.</span></span> <span data-ttu-id="c163d-130">Nazwa klasy i pliku jest taka sama jak nazwa *WMIClass.*</span><span class="sxs-lookup"><span data-stu-id="c163d-130">The name of the class and the file are the same as the name of the *WMIClass.*</span></span> <span data-ttu-id="c163d-131">Jeśli *WMIClass* zawiera znak podkreślenia, narzędzie używa części nazwy klasy po znaku podkreślenia.</span><span class="sxs-lookup"><span data-stu-id="c163d-131">If *WMIClass* contains an underscore character, the tool uses the part of the class name following the underscore character.</span></span> <span data-ttu-id="c163d-132">Na przykład jeśli nazwa *WMIClass* ma format **Win32_LogicalDisk**, wygenerowana Klasa i plik o nazwie "dysk logiczny".</span><span class="sxs-lookup"><span data-stu-id="c163d-132">For example, if the *WMIClass* name is in the format **Win32_LogicalDisk**, the generated class and file is named "logicaldisk".</span></span> <span data-ttu-id="c163d-133">Jeżeli plik już istnieje, narzędzie zastąpi istniejący plik.</span><span class="sxs-lookup"><span data-stu-id="c163d-133">If a file already exists, the tool overwrites the existing file.</span></span>|  
|<span data-ttu-id="c163d-134">**/PW** *hasła*</span><span class="sxs-lookup"><span data-stu-id="c163d-134">**/pw**  *password*</span></span>|<span data-ttu-id="c163d-135">Określa hasło, które ma być używane podczas logowania do komputera określonego przez **/m** Option.</span><span class="sxs-lookup"><span data-stu-id="c163d-135">Specifies the password to use when logging on to a computer specified by the **/m** option.</span></span>|  
|<span data-ttu-id="c163d-136">**/u** *nazwy użytkownika*</span><span class="sxs-lookup"><span data-stu-id="c163d-136">**/u**  *user name*</span></span>|<span data-ttu-id="c163d-137">Określa nazwę użytkownika, która ma być używana podczas logowania do komputera określonego przez **/m** Option.</span><span class="sxs-lookup"><span data-stu-id="c163d-137">Specifies the user name to use when logging on to a computer specified by the **/m** option.</span></span>|  
|<span data-ttu-id="c163d-138">**/?**</span><span class="sxs-lookup"><span data-stu-id="c163d-138">**/?**</span></span>|<span data-ttu-id="c163d-139">Wyświetla składnię polecenia i opcje narzędzia.</span><span class="sxs-lookup"><span data-stu-id="c163d-139">Displays command syntax and options for the tool.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="c163d-140">Uwagi</span><span class="sxs-lookup"><span data-stu-id="c163d-140">Remarks</span></span>  
 <span data-ttu-id="c163d-141">Mgmtclassgen. exe używa <xref:System.Management.ManagementClass.GetStronglyTypedClassCode%2A?displayProperty=nameWithType> metody.</span><span class="sxs-lookup"><span data-stu-id="c163d-141">Mgmtclassgen.exe uses the <xref:System.Management.ManagementClass.GetStronglyTypedClassCode%2A?displayProperty=nameWithType> method.</span></span> <span data-ttu-id="c163d-142">Dzięki temu można użyć dowolnego niestandardowego dostawcy kodu, aby wygenerować kod w zarządzanych językach innych niż C#, Visual Basic i JScript.</span><span class="sxs-lookup"><span data-stu-id="c163d-142">Therefore, you can use any custom code provider to generate code in managed languages other than C#, Visual Basic, and JScript.</span></span>  
  
 <span data-ttu-id="c163d-143">Należy zauważyć, że wygenerowane klasy są powiązane ze schematem, dla którego są generowane.</span><span class="sxs-lookup"><span data-stu-id="c163d-143">Note that generated classes are bound to the schema for which they are generated.</span></span> <span data-ttu-id="c163d-144">Jeśli schemat źródłowy ulegnie zmianie, trzeba ponownie wygenerować klasę, jeśli chce się odzwierciedlić zmiany w schemacie.</span><span class="sxs-lookup"><span data-stu-id="c163d-144">If the underlying schema changes, you must regenerate the class if you want it to reflect changes to the schema.</span></span>  
  
 <span data-ttu-id="c163d-145">W poniższej tabeli pokazano mapowanie typów modelu wspólnych informacji (CIM) usługi WMI na typy danych w generowanej klasie:</span><span class="sxs-lookup"><span data-stu-id="c163d-145">The following table shows how WMI Common Information Model (CIM) types map to data types in a generated class:</span></span>  
  
|<span data-ttu-id="c163d-146">Typ modelu CIM</span><span class="sxs-lookup"><span data-stu-id="c163d-146">CIM type</span></span>|<span data-ttu-id="c163d-147">Typ danych w generowanej klasie</span><span class="sxs-lookup"><span data-stu-id="c163d-147">Data type in the generated class</span></span>|  
|--------------|--------------------------------------|  
|<span data-ttu-id="c163d-148">CIM_SINT8</span><span class="sxs-lookup"><span data-stu-id="c163d-148">CIM_SINT8</span></span>|<span data-ttu-id="c163d-149">**SByte**</span><span class="sxs-lookup"><span data-stu-id="c163d-149">**SByte**</span></span>|  
|<span data-ttu-id="c163d-150">CIM_UINT8</span><span class="sxs-lookup"><span data-stu-id="c163d-150">CIM_UINT8</span></span>|<span data-ttu-id="c163d-151">**Byte**</span><span class="sxs-lookup"><span data-stu-id="c163d-151">**Byte**</span></span>|  
|<span data-ttu-id="c163d-152">CIM_SINT16</span><span class="sxs-lookup"><span data-stu-id="c163d-152">CIM_SINT16</span></span>|<span data-ttu-id="c163d-153">**Int16**</span><span class="sxs-lookup"><span data-stu-id="c163d-153">**Int16**</span></span>|  
|<span data-ttu-id="c163d-154">CIM_UINT16</span><span class="sxs-lookup"><span data-stu-id="c163d-154">CIM_UINT16</span></span>|<span data-ttu-id="c163d-155">**UInt16**</span><span class="sxs-lookup"><span data-stu-id="c163d-155">**UInt16**</span></span>|  
|<span data-ttu-id="c163d-156">CIM_SINT32</span><span class="sxs-lookup"><span data-stu-id="c163d-156">CIM_SINT32</span></span>|<span data-ttu-id="c163d-157">**Int32**</span><span class="sxs-lookup"><span data-stu-id="c163d-157">**Int32**</span></span>|  
|<span data-ttu-id="c163d-158">SIM_UINT32</span><span class="sxs-lookup"><span data-stu-id="c163d-158">SIM_UINT32</span></span>|<span data-ttu-id="c163d-159">**Równ**</span><span class="sxs-lookup"><span data-stu-id="c163d-159">**UInt32**</span></span>|  
|<span data-ttu-id="c163d-160">CIM_SINT64</span><span class="sxs-lookup"><span data-stu-id="c163d-160">CIM_SINT64</span></span>|<span data-ttu-id="c163d-161">**Int64**</span><span class="sxs-lookup"><span data-stu-id="c163d-161">**Int64**</span></span>|  
|<span data-ttu-id="c163d-162">CIM_UINT64</span><span class="sxs-lookup"><span data-stu-id="c163d-162">CIM_UINT64</span></span>|<span data-ttu-id="c163d-163">**UInt64**</span><span class="sxs-lookup"><span data-stu-id="c163d-163">**UInt64**</span></span>|  
|<span data-ttu-id="c163d-164">CIM_REAL32</span><span class="sxs-lookup"><span data-stu-id="c163d-164">CIM_REAL32</span></span>|<span data-ttu-id="c163d-165">**Single**</span><span class="sxs-lookup"><span data-stu-id="c163d-165">**Single**</span></span>|  
|<span data-ttu-id="c163d-166">CIM_REAL64</span><span class="sxs-lookup"><span data-stu-id="c163d-166">CIM_REAL64</span></span>|<span data-ttu-id="c163d-167">**Double**</span><span class="sxs-lookup"><span data-stu-id="c163d-167">**Double**</span></span>|  
|<span data-ttu-id="c163d-168">CIM_BOOLEAN</span><span class="sxs-lookup"><span data-stu-id="c163d-168">CIM_BOOLEAN</span></span>|<span data-ttu-id="c163d-169">**Boolean**</span><span class="sxs-lookup"><span data-stu-id="c163d-169">**Boolean**</span></span>|  
|<span data-ttu-id="c163d-170">CIM_String</span><span class="sxs-lookup"><span data-stu-id="c163d-170">CIM_String</span></span>|<span data-ttu-id="c163d-171">**Ciąg**</span><span class="sxs-lookup"><span data-stu-id="c163d-171">**String**</span></span>|  
|<span data-ttu-id="c163d-172">CIM_DATETIME</span><span class="sxs-lookup"><span data-stu-id="c163d-172">CIM_DATETIME</span></span>|<span data-ttu-id="c163d-173">**DateTime** lub **TimeSpan**</span><span class="sxs-lookup"><span data-stu-id="c163d-173">**DateTime** or **TimeSpan**</span></span>|  
|<span data-ttu-id="c163d-174">CIM_REFERENCE</span><span class="sxs-lookup"><span data-stu-id="c163d-174">CIM_REFERENCE</span></span>|<span data-ttu-id="c163d-175">**ManagementPath**</span><span class="sxs-lookup"><span data-stu-id="c163d-175">**ManagementPath**</span></span>|  
|<span data-ttu-id="c163d-176">CIM_CHAR16</span><span class="sxs-lookup"><span data-stu-id="c163d-176">CIM_CHAR16</span></span>|<span data-ttu-id="c163d-177">**Delikatn**</span><span class="sxs-lookup"><span data-stu-id="c163d-177">**Char**</span></span>|  
|<span data-ttu-id="c163d-178">CIM_OBJECT</span><span class="sxs-lookup"><span data-stu-id="c163d-178">CIM_OBJECT</span></span>|<span data-ttu-id="c163d-179">**ManagementBaseObject**</span><span class="sxs-lookup"><span data-stu-id="c163d-179">**ManagementBaseObject**</span></span>|  
|<span data-ttu-id="c163d-180">CIM_IUNKNOWN</span><span class="sxs-lookup"><span data-stu-id="c163d-180">CIM_IUNKNOWN</span></span>|<span data-ttu-id="c163d-181">**Obiekt**</span><span class="sxs-lookup"><span data-stu-id="c163d-181">**Object**</span></span>|  
|<span data-ttu-id="c163d-182">CIM_ARRAY</span><span class="sxs-lookup"><span data-stu-id="c163d-182">CIM_ARRAY</span></span>|<span data-ttu-id="c163d-183">Tablica wymienionych powyżej obiektów</span><span class="sxs-lookup"><span data-stu-id="c163d-183">Array of the above mentioned objects</span></span>|  
  
 <span data-ttu-id="c163d-184">Podczas generowania klasy WMI należy zwrócić uwagę na następujące zachowania:</span><span class="sxs-lookup"><span data-stu-id="c163d-184">Note the following behaviors when you generate a WMI class:</span></span>  
  
- <span data-ttu-id="c163d-185">Możliwe jest, że standardowa publiczna właściwość lub metoda będzie miała taką samą nazwę jak istniejąca właściwość lub metoda.</span><span class="sxs-lookup"><span data-stu-id="c163d-185">It is possible for a standard public property or method to have the same name as an existing property or method.</span></span> <span data-ttu-id="c163d-186">Jeśli tak się zdarzy, narzędzie zmieni nazwę właściwości lub metody w generowanej klasie w celu uniknięcia konfliktu nazw.</span><span class="sxs-lookup"><span data-stu-id="c163d-186">If this occurs, the tool changes the name of the property or method in the generated class to avoid naming conflicts.</span></span>  
  
- <span data-ttu-id="c163d-187">Możliwe jest, że nazwa właściwości lub metody w generowanej klasie będzie słowem kluczowym w docelowym języku programowania.</span><span class="sxs-lookup"><span data-stu-id="c163d-187">It is possible for the name of a property or method in a generated class to be a keyword in the target programming language.</span></span> <span data-ttu-id="c163d-188">Jeśli tak się zdarzy, narzędzie zmieni nazwę właściwości lub metody w generowanej klasie w celu uniknięcia konfliktu nazw.</span><span class="sxs-lookup"><span data-stu-id="c163d-188">If this occurs, the tool changes the name of the property or method in the generated class to avoid naming conflicts.</span></span>  
  
- <span data-ttu-id="c163d-189">W usłudze WMI kwalifikatory to modyfikatory zawierające informacje opisujące klasę, wystąpienie, właściwość lub metodę.</span><span class="sxs-lookup"><span data-stu-id="c163d-189">In WMI, qualifiers are modifiers that contain information to describe a class, instance, property, or method.</span></span> <span data-ttu-id="c163d-190">Usługa WMI używa kwalifikatorów standardowych, takich jak **Odczyt**, **zapis**i **klucz** , aby opisać właściwość w wygenerowanej klasie.</span><span class="sxs-lookup"><span data-stu-id="c163d-190">WMI uses standard qualifiers such as **Read**, **Write**, and **Key** to describe a property in a generated class.</span></span> <span data-ttu-id="c163d-191">Na przykład właściwość, która jest modyfikowana przy użyciu kwalifikatora **odczytu** , jest definiowana tylko przy użyciu metody dostępu **Get** właściwości w wygenerowanej klasie.</span><span class="sxs-lookup"><span data-stu-id="c163d-191">For example, a property that is modified with a **Read** qualifier is defined only with a property **get** accessor in the generated class.</span></span> <span data-ttu-id="c163d-192">Ponieważ właściwość oznaczona kwalifikatorem **odczytu** jest przeznaczona tylko do odczytu, metoda dostępu **Set** nie jest zdefiniowana.</span><span class="sxs-lookup"><span data-stu-id="c163d-192">Because a property marked with the **Read** qualifier is intended to be read-only, a **set** accessor is not defined.</span></span>  
  
- <span data-ttu-id="c163d-193">Właściwość numeryczna może być modyfikowana przez kwalifikatory **wartości** i **ValueMaps** , aby wskazać, że właściwość można ustawić tylko dla określonych dozwolonych wartości.</span><span class="sxs-lookup"><span data-stu-id="c163d-193">A numeric property can be modified by the **Values** and **ValueMaps** qualifiers to indicate that the property can be set only to specified permissible values.</span></span> <span data-ttu-id="c163d-194">Wyliczenie jest generowane z tymi **wartościami** i **ValueMaps** , a właściwość jest zamapowana na Wyliczenie.</span><span class="sxs-lookup"><span data-stu-id="c163d-194">An enumeration is generated with these **Values** and **ValueMaps** and the property is mapped to the enumeration.</span></span>  
  
- <span data-ttu-id="c163d-195">Usługa WMI używa pojedynczego terminu w celu opisania klasy, która ma tylko jedno wystąpienie.</span><span class="sxs-lookup"><span data-stu-id="c163d-195">The WMI uses the term singleton to describe a class that can have only one instance.</span></span> <span data-ttu-id="c163d-196">W związku z tym, Konstruktor bez parametrów dla klasy pojedynczej będzie inicjować klasę tylko do wystąpienia klasy.</span><span class="sxs-lookup"><span data-stu-id="c163d-196">Therefore, the parameterless constructor for a singleton class will initialize the class to the only instance of the class.</span></span>  
  
- <span data-ttu-id="c163d-197">Klasa WMI może mieć właściwości, które są obiektami.</span><span class="sxs-lookup"><span data-stu-id="c163d-197">A WMI class can have properties that are objects.</span></span> <span data-ttu-id="c163d-198">Podczas generowania silnie typizowanej klasy dla klasy WMI tego typu należy wziąć pod uwagę wygenerowanie silnie typizowanych klas dla typów właściwości osadzonych obiektów.</span><span class="sxs-lookup"><span data-stu-id="c163d-198">When you generate a strongly-typed class for this type of WMI class, you should consider generating strongly-typed classes for the types of the embedded object properties.</span></span> <span data-ttu-id="c163d-199">Umożliwi to dostęp do osadzonych obiektów w silnie typizowany sposób.</span><span class="sxs-lookup"><span data-stu-id="c163d-199">This will allow you to access the embedded objects in a strongly-typed manner.</span></span> <span data-ttu-id="c163d-200">Należy zauważyć, że wygenerowany kod może nie być w stanie wykryć typu osadzonego obiektu.</span><span class="sxs-lookup"><span data-stu-id="c163d-200">Note that the generated code might not be able to detect the type of the embedded object.</span></span> <span data-ttu-id="c163d-201">W takim przypadku w wygenerowanym kodzie zostanie utworzony komentarz powiadamiający o problemie.</span><span class="sxs-lookup"><span data-stu-id="c163d-201">In this case, a comment will be created in the generated code to notify you of this issue.</span></span> <span data-ttu-id="c163d-202">Następnie można zmodyfikować wygenerowany kod, tak aby właściwość miała typ innej generowanej klasy.</span><span class="sxs-lookup"><span data-stu-id="c163d-202">You can then modify the generated code to type the property to the other generated class.</span></span>  
  
- <span data-ttu-id="c163d-203">W usłudze WMI wartość danych typu CIM_DATETIME może przedstawiać określoną datę i godzinę albo interwał czasu.</span><span class="sxs-lookup"><span data-stu-id="c163d-203">In WMI, the data value of the CIM_DATETIME data type can represent either a specific date and time or a time interval.</span></span> <span data-ttu-id="c163d-204">Jeśli wartość danych reprezentuje datę i godzinę, typem danych w generowanej klasie jest **DateTime**.</span><span class="sxs-lookup"><span data-stu-id="c163d-204">If the data value represents a date and time, the data type in the generated class is **DateTime**.</span></span> <span data-ttu-id="c163d-205">Jeśli wartość danych reprezentuje przedział czasu, typem danych w generowanej klasie jest **TimeSpan**.</span><span class="sxs-lookup"><span data-stu-id="c163d-205">If the data value represents a time interval, the data type in the generated class is **TimeSpan**.</span></span>  
  
 <span data-ttu-id="c163d-206">Alternatywnie można wygenerować silnie typizowaną klasę, używając rozszerzenia zarządzania Eksploratora serwera w programie Visual Studio .NET.</span><span class="sxs-lookup"><span data-stu-id="c163d-206">You can alternately generate a strongly-typed class using the Server Explorer Management Extension in Visual Studio .NET.</span></span>  
  
 <span data-ttu-id="c163d-207">Aby uzyskać więcej informacji na temat usługi WMI, zobacz temat **Instrumentacja zarządzania Windows** w dokumentacji zestawu SDK platformy.</span><span class="sxs-lookup"><span data-stu-id="c163d-207">For more information about WMI, see the **Windows Management Instrumentation** topic in the Platform SDK documentation.</span></span>  
  
## <a name="examples"></a><span data-ttu-id="c163d-208">Przykłady</span><span class="sxs-lookup"><span data-stu-id="c163d-208">Examples</span></span>  
 <span data-ttu-id="c163d-209">Następujące polecenie generuje klasę zarządzaną w C# kodzie dla klasy WMI usługi **Win32_LogicalDisk** w przestrzeni nazw **root\cimv2** .</span><span class="sxs-lookup"><span data-stu-id="c163d-209">The following command generates a managed class in C# code for the **Win32_LogicalDisk** WMI class in the **Root\cimv2** namespace.</span></span> <span data-ttu-id="c163d-210">Narzędzie zapisuje klasę zarządzaną w pliku źródłowym w c:\disk.cs w **katalogu głównym. CIMV2.** Przestrzeń nazw Win32.</span><span class="sxs-lookup"><span data-stu-id="c163d-210">The tool writes the managed class to the source file at c:\disk.cs in the **ROOT.CIMV2.Win32** namespace.</span></span>  
  
```  
mgmtclassgen Win32_LogicalDisk /n root\cimv2 /l CS /p c:\disk.cs  
```  
  
 <span data-ttu-id="c163d-211">W poniższym przykładzie kodu pokazano, w jaki sposób można programowo używać wygenerowanej klasy.</span><span class="sxs-lookup"><span data-stu-id="c163d-211">The following code example shows how to use a generated class programmatically.</span></span> <span data-ttu-id="c163d-212">Najpierw jest wyliczane wystąpienie klasy i jest drukowana ścieżka.</span><span class="sxs-lookup"><span data-stu-id="c163d-212">First, an instance of the class is enumerated and the path is printed.</span></span> <span data-ttu-id="c163d-213">Następnie za pomocą wystąpienia usługi WMI jest tworzone wystąpienie wygenerowanej klasy, które ma zostać zainicjowane.</span><span class="sxs-lookup"><span data-stu-id="c163d-213">Next, an instance of the generated class to be initialized is created with an instance of WMI.</span></span> <span data-ttu-id="c163d-214">`Process`jest klasą wygenerowaną  dla Win32_Process `LogicalDisk` i jest klasą wygenerowaną dla klasy **Win32_LogicalDisk** w przestrzeni nazw **root\cimv2** .</span><span class="sxs-lookup"><span data-stu-id="c163d-214">`Process` is the class generated for **Win32_Process** and `LogicalDisk` is the class generated for **Win32_LogicalDisk** in the **Root\cimv2** namespace.</span></span>  
  
```vb  
Imports System  
Imports System.Management  
Imports ROOT.CIMV2.Win32  
  
Public Class App     
   Public Shared Sub Main()        
      ' Enumerate instances of the Win32_process.  
      ' Print the Name property of the instance.  
      Dim ps As Process     
      For Each ps In  Process.GetInstances()  
         Console.WriteLine(ps.Name)  
      Next ps  
  
      ' Initialize the instance of LogicalDisk with  
      ' the WMI instance pointing to logical drive d:.  
      Dim dskD As New LogicalDisk(New _  
         ManagementPath("win32_LogicalDisk.DeviceId=""d:"""))  
      Console.WriteLine(dskD.Caption)  
   End Sub  
End Class  
```  
  
```csharp  
using System;  
using System.Management;  
using ROOT.CIMV2.Win32;  
  
public class App  
{  
   public static void Main()  
   {  
      // Enumerate instances of the Win32_process.  
      // Print the Name property of the instance.  
      foreach(Process ps in Process.GetInstances())  
      {  
         Console.WriteLine(ps.Name);  
      }  
  
      // Initialize the instance of LogicalDisk with  
      // the WMI instance pointing to logical drive d:.  
      LogicalDisk dskD = new LogicalDisk(new ManagementPath(  
        "win32_LogicalDisk.DeviceId=\"d:\""));  
      Console.WriteLine(dskD.Caption);  
   }  
}  
```  
  
## <a name="see-also"></a><span data-ttu-id="c163d-215">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="c163d-215">See also</span></span>

- <xref:System.Management>
- <xref:System.Management.ManagementClass.GetStronglyTypedClassCode%2A?displayProperty=nameWithType>
- <xref:System.CodeDom.Compiler.CodeDomProvider?displayProperty=nameWithType>
- [<span data-ttu-id="c163d-216">Narzędzia</span><span class="sxs-lookup"><span data-stu-id="c163d-216">Tools</span></span>](../../../docs/framework/tools/index.md)
- [<span data-ttu-id="c163d-217">Wiersze polecenia</span><span class="sxs-lookup"><span data-stu-id="c163d-217">Command Prompts</span></span>](../../../docs/framework/tools/developer-command-prompt-for-vs.md)

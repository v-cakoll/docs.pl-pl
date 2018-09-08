---
title: 'Porady: zapisywanie stref czasowych w zasobie osadzonym'
ms.date: 04/10/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- time zones [.NET Framework], saving
- time zone objects [.NET Framework], serializing
- time zone objects [.NET Framework], saving
ms.assetid: 3c96d83a-a057-4496-abb0-8f4b12712558
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 921874e774d18751c29db495dac1bc53d10cc8ad
ms.sourcegitcommit: c7f3e2e9d6ead6cc3acd0d66b10a251d0c66e59d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/08/2018
ms.locfileid: "44211856"
---
# <a name="how-to-save-time-zones-to-an-embedded-resource"></a><span data-ttu-id="c4f99-102">Porady: zapisywanie stref czasowych w zasobie osadzonym</span><span class="sxs-lookup"><span data-stu-id="c4f99-102">How to: Save time zones to an embedded resource</span></span>

<span data-ttu-id="c4f99-103">Często uwzględniających strefy czasowe aplikacji wymaga obecności daną strefę czasową.</span><span class="sxs-lookup"><span data-stu-id="c4f99-103">A time zone-aware application often requires the presence of a particular time zone.</span></span> <span data-ttu-id="c4f99-104">Jednakże ponieważ dostępność poszczególnych <xref:System.TimeZoneInfo> obiektów zależy od informacji przechowywanych w rejestrze systemu lokalnego, nawet zwyczajowo dostępnych stref czasowych mogą być nieobecne.</span><span class="sxs-lookup"><span data-stu-id="c4f99-104">However, because the availability of individual <xref:System.TimeZoneInfo> objects depends on information stored in the local system's registry, even customarily available time zones may be absent.</span></span> <span data-ttu-id="c4f99-105">Ponadto informacje o niestandardowych stref czasowych są tworzone za pomocą <xref:System.TimeZoneInfo.CreateCustomTimeZone%2A> metoda nie jest przechowywany wraz z innymi informacjami strefy czasowej w rejestrze.</span><span class="sxs-lookup"><span data-stu-id="c4f99-105">In addition, information about custom time zones instantiated by using the <xref:System.TimeZoneInfo.CreateCustomTimeZone%2A> method is not stored with other time zone information in the registry.</span></span> <span data-ttu-id="c4f99-106">Aby upewnić się, że tych stref czasowych są dostępne, gdy są potrzebne, można je zapisać, szeregując je i je później przywrócić przez ich deserializacji.</span><span class="sxs-lookup"><span data-stu-id="c4f99-106">To ensure that these time zones are available when they are needed, you can save them by serializing them, and later restore them by deserializing them.</span></span>

<span data-ttu-id="c4f99-107">Zazwyczaj serializacji <xref:System.TimeZoneInfo> obiekt występuje oprócz aplikacji uwzględniających strefy czasowe.</span><span class="sxs-lookup"><span data-stu-id="c4f99-107">Typically, serializing a <xref:System.TimeZoneInfo> object occurs apart from the time zone-aware application.</span></span> <span data-ttu-id="c4f99-108">W zależności od magazynu danych, używane do przechowywania Zserializowany <xref:System.TimeZoneInfo> obiektów, może być serializowany danych strefa czasowa, jako część procedury lub instalacyjnego (na przykład, gdy dane są przechowywane w kluczu rejestru aplikacji) lub jako część procedury narzędzia, która jest uruchamiana przed ostatnim aplikacja jest kompilowana, (na przykład, kiedy serializowane dane są przechowywane w pliku zasobów (.resx) XML platformy .NET).</span><span class="sxs-lookup"><span data-stu-id="c4f99-108">Depending on the data store used to hold serialized <xref:System.TimeZoneInfo> objects, time zone data may be serialized as part of a setup or installation routine (for example, when the data is stored in an application key of the registry), or as part of a utility routine that runs before the final application is compiled (for example, when the serialized data is stored in a .NET XML resource (.resx) file).</span></span>

<span data-ttu-id="c4f99-109">Oprócz pliku zasobów, który jest kompilowany razem z aplikacją kilka innych magazynów danych może służyć do informacji o strefie czasowej.</span><span class="sxs-lookup"><span data-stu-id="c4f99-109">In addition to a resource file that is compiled with the application, several other data stores can be used for time zone information.</span></span> <span data-ttu-id="c4f99-110">Należą do nich między innymi:</span><span class="sxs-lookup"><span data-stu-id="c4f99-110">These include the following:</span></span>

* <span data-ttu-id="c4f99-111">Rejestr.</span><span class="sxs-lookup"><span data-stu-id="c4f99-111">The registry.</span></span> <span data-ttu-id="c4f99-112">Należy pamiętać, że aplikacja powinna używać podkluczy klucza własnej aplikacji do przechowywania danych niestandardowa strefa czasowa, a nie przy użyciu podkluczy HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Windows NT\CurrentVersion\Time strefy.</span><span class="sxs-lookup"><span data-stu-id="c4f99-112">Note that an application should use the subkeys of its own application key to store custom time zone data rather than using the subkeys of HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Windows NT\CurrentVersion\Time Zones.</span></span>

* <span data-ttu-id="c4f99-113">Pliki konfiguracji.</span><span class="sxs-lookup"><span data-stu-id="c4f99-113">Configuration files.</span></span>

* <span data-ttu-id="c4f99-114">Inne pliki systemowe.</span><span class="sxs-lookup"><span data-stu-id="c4f99-114">Other system files.</span></span>

### <a name="to-save-a-time-zone-by-serializing-it-to-a-resx-file"></a><span data-ttu-id="c4f99-115">Aby zapisać strefy czasowej, szeregując go na plik Resx</span><span class="sxs-lookup"><span data-stu-id="c4f99-115">To save a time zone by serializing it to a .resx file</span></span>

1. <span data-ttu-id="c4f99-116">Pobieranie istniejącej strefy czasowej, lub Utwórz nową strefę czasu.</span><span class="sxs-lookup"><span data-stu-id="c4f99-116">Retrieve an existing time zone or create a new time zone.</span></span>

   <span data-ttu-id="c4f99-117">Aby pobrać istniejącej strefy czasowej, zobacz [porady: dostęp do wstępnie zdefiniowanych obiektów stref UTC i czasem lokalnym](../../../docs/standard/datetime/access-utc-and-local.md) i [jak: Tworzenie wystąpień obiektów TimeZoneInfo](../../../docs/standard/datetime/instantiate-time-zone-info.md).</span><span class="sxs-lookup"><span data-stu-id="c4f99-117">To retrieve an existing time zone, see [How to: Access the predefined UTC and local time zone objects](../../../docs/standard/datetime/access-utc-and-local.md) and [How to: Instantiate a TimeZoneInfo object](../../../docs/standard/datetime/instantiate-time-zone-info.md).</span></span>

   <span data-ttu-id="c4f99-118">Aby utworzyć nowej strefy czasowej, wywołaj jednego z przeciążeń <xref:System.TimeZoneInfo.CreateCustomTimeZone%2A> metody.</span><span class="sxs-lookup"><span data-stu-id="c4f99-118">To create a new time zone, call one of the overloads of the <xref:System.TimeZoneInfo.CreateCustomTimeZone%2A> method.</span></span> <span data-ttu-id="c4f99-119">Aby uzyskać więcej informacji, zobacz [porady: tworzenie stref czasowych bez reguł korygowania](../../../docs/standard/datetime/create-time-zones-without-adjustment-rules.md) i [porady: tworzenie stref czasowych przy użyciu reguł korygowania](../../../docs/standard/datetime/create-time-zones-with-adjustment-rules.md).</span><span class="sxs-lookup"><span data-stu-id="c4f99-119">For more information, see [How to: Create time zones without adjustment rules](../../../docs/standard/datetime/create-time-zones-without-adjustment-rules.md) and [How to: Create time zones with adjustment rules](../../../docs/standard/datetime/create-time-zones-with-adjustment-rules.md).</span></span>

2. <span data-ttu-id="c4f99-120">Wywołaj <xref:System.TimeZoneInfo.ToSerializedString%2A> metodę, aby utworzyć ciąg, który zawiera dane strefy czasowej.</span><span class="sxs-lookup"><span data-stu-id="c4f99-120">Call the <xref:System.TimeZoneInfo.ToSerializedString%2A> method to create a string that contains the time zone's data.</span></span>

3. <span data-ttu-id="c4f99-121">Utwórz wystąpienie <xref:System.IO.StreamWriter> obiektu, podając nazwę i opcjonalnie ścieżkę pliku ResX można <xref:System.IO.StreamWriter> konstruktora klasy.</span><span class="sxs-lookup"><span data-stu-id="c4f99-121">Instantiate a <xref:System.IO.StreamWriter> object by providing the name and optionally the path of the .resx file to the <xref:System.IO.StreamWriter> class constructor.</span></span>

4. <span data-ttu-id="c4f99-122">Utwórz wystąpienie <xref:System.Resources.ResXResourceWriter> obiektu przez przekazanie <xref:System.IO.StreamWriter> obiekt <xref:System.Resources.ResXResourceWriter> konstruktora klasy.</span><span class="sxs-lookup"><span data-stu-id="c4f99-122">Instantiate a <xref:System.Resources.ResXResourceWriter> object by passing the <xref:System.IO.StreamWriter> object to the <xref:System.Resources.ResXResourceWriter> class constructor.</span></span>

5. <span data-ttu-id="c4f99-123">Przebieg strefę czasową serializować ciągu do <xref:System.Resources.ResXResourceWriter.AddResource%2A?displayProperty=nameWithType> metody.</span><span class="sxs-lookup"><span data-stu-id="c4f99-123">Pass the time zone's serialized string to the <xref:System.Resources.ResXResourceWriter.AddResource%2A?displayProperty=nameWithType> method.</span></span>

6. <span data-ttu-id="c4f99-124">Wywołaj <xref:System.Resources.ResXResourceWriter.Generate%2A?displayProperty=nameWithType> metody.</span><span class="sxs-lookup"><span data-stu-id="c4f99-124">Call the <xref:System.Resources.ResXResourceWriter.Generate%2A?displayProperty=nameWithType> method.</span></span>

7. <span data-ttu-id="c4f99-125">Wywołaj <xref:System.Resources.ResXResourceWriter.Close%2A?displayProperty=nameWithType> metody.</span><span class="sxs-lookup"><span data-stu-id="c4f99-125">Call the <xref:System.Resources.ResXResourceWriter.Close%2A?displayProperty=nameWithType> method.</span></span>

8. <span data-ttu-id="c4f99-126">Zamknij <xref:System.IO.StreamWriter> obiektu przez wywołanie jego <xref:System.IO.StreamWriter.Close%2A> metody.</span><span class="sxs-lookup"><span data-stu-id="c4f99-126">Close the <xref:System.IO.StreamWriter> object by calling its <xref:System.IO.StreamWriter.Close%2A> method.</span></span>

9. <span data-ttu-id="c4f99-127">Dodaj plik Resx wygenerowane do projektu programu Visual Studio w aplikacji.</span><span class="sxs-lookup"><span data-stu-id="c4f99-127">Add the generated .resx file to the application's Visual Studio project.</span></span>

10. <span data-ttu-id="c4f99-128">Za pomocą **właściwości** okna w programie Visual Studio, upewnij się, że plik Resx **Build Action** właściwość jest ustawiona na **zasób osadzony**.</span><span class="sxs-lookup"><span data-stu-id="c4f99-128">Using the **Properties** window in Visual Studio, make sure that the .resx file's **Build Action** property is set to **Embedded Resource**.</span></span>

## <a name="example"></a><span data-ttu-id="c4f99-129">Przykład</span><span class="sxs-lookup"><span data-stu-id="c4f99-129">Example</span></span>

<span data-ttu-id="c4f99-130">Poniższy przykład szereguje <xref:System.TimeZoneInfo> obiekt, który reprezentuje Środkowa (czas standardowy) i <xref:System.TimeZoneInfo> obiekt, który reprezentuje czas Antarktyda, stacja Palmer .NET XML pliku zasobu, który nosi nazwę SerializedTimeZones.resx.</span><span class="sxs-lookup"><span data-stu-id="c4f99-130">The following example serializes a <xref:System.TimeZoneInfo> object that represents Central Standard Time and a <xref:System.TimeZoneInfo> object that represents the Palmer Station, Antarctica time to a .NET XML resource file that is named SerializedTimeZones.resx.</span></span> <span data-ttu-id="c4f99-131">Środkowy czas standardowy zwykle definiuje się w rejestrze. Antarktyda, stacja Palmer jest niestandardowa strefa czasowa.</span><span class="sxs-lookup"><span data-stu-id="c4f99-131">Central Standard Time is typically defined in the registry; Palmer Station, Antarctica is a custom time zone.</span></span>

[!code-csharp[TimeZone2.Serialization#1](../../../samples/snippets/csharp/VS_Snippets_CLR/TimeZone2.Serialization/cs/SerializeTimeZoneData.cs#1)]
[!code-vb[TimeZone2.Serialization#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/TimeZone2.Serialization/vb/SerializeTimeZoneData.vb#1)]

<span data-ttu-id="c4f99-132">W tym przykładzie serializuje <xref:System.TimeZoneInfo> obiektów, tak aby były dostępne w pliku zasobów w czasie kompilacji.</span><span class="sxs-lookup"><span data-stu-id="c4f99-132">This example serializes <xref:System.TimeZoneInfo> objects so that they are available in a resource file at compile time.</span></span>

<span data-ttu-id="c4f99-133">Ponieważ <xref:System.Resources.ResXResourceWriter.Generate%2A?displayProperty=nameWithType> metoda dodaje informacje o nagłówku pełną plikowi zasób XML platformy .NET, nie można dodać zasoby do istniejącego pliku.</span><span class="sxs-lookup"><span data-stu-id="c4f99-133">Because the <xref:System.Resources.ResXResourceWriter.Generate%2A?displayProperty=nameWithType> method adds complete header information to a .NET XML resource file, it cannot be used to add resources to an existing file.</span></span> <span data-ttu-id="c4f99-134">Przykład wykonuje tę przez sprawdzenie, czy plik SerializedTimeZones.resx, i jeśli istnieje, przechowywaniu wszystkich jej zasobów innych niż dwa serializacji strefach czasowych prawidłowo ogólnego <xref:System.Collections.Generic.Dictionary%602> obiektu.</span><span class="sxs-lookup"><span data-stu-id="c4f99-134">The example handles this by checking for the SerializedTimeZones.resx file and, if it exists, storing all of its resources other than the two serialized time zones to a generic <xref:System.Collections.Generic.Dictionary%602> object.</span></span> <span data-ttu-id="c4f99-135">Istniejący plik jest usuwany i istniejące zasoby są dodawane do nowego pliku SerializedTimeZones.resx.</span><span class="sxs-lookup"><span data-stu-id="c4f99-135">The existing file is then deleted and the existing resources are added to a new SerializedTimeZones.resx file.</span></span> <span data-ttu-id="c4f99-136">Dane serializowane strefa czasowa jest także dodawane do tego pliku.</span><span class="sxs-lookup"><span data-stu-id="c4f99-136">The serialized time zone data is also added to this file.</span></span>

<span data-ttu-id="c4f99-137">Klucz (lub **nazwa**) pola zasobów nie może zawierać spacji osadzonych.</span><span class="sxs-lookup"><span data-stu-id="c4f99-137">The key (or **Name**) fields of resources should not contain embedded spaces.</span></span> <span data-ttu-id="c4f99-138"><xref:System.String.Replace%28System.String%2CSystem.String%29> Metoda jest wywoływana, aby usunąć wszystkie spacje w identyfikatorach strefę czasową, przed przypisaniem do pliku zasobów.</span><span class="sxs-lookup"><span data-stu-id="c4f99-138">The <xref:System.String.Replace%28System.String%2CSystem.String%29> method is called to remove all embedded spaces in the time zone identifiers before they are assigned to the resource file.</span></span>

## <a name="compiling-the-code"></a><span data-ttu-id="c4f99-139">Kompilowanie kodu</span><span class="sxs-lookup"><span data-stu-id="c4f99-139">Compiling the code</span></span>

<span data-ttu-id="c4f99-140">Ten przykład wymaga:</span><span class="sxs-lookup"><span data-stu-id="c4f99-140">This example requires:</span></span>

* <span data-ttu-id="c4f99-141">Odwołanie do System.Windows.Forms.dll i System.Core.dll dodania do projektu.</span><span class="sxs-lookup"><span data-stu-id="c4f99-141">That a reference to System.Windows.Forms.dll and System.Core.dll be added to the project.</span></span>

* <span data-ttu-id="c4f99-142">Czy następujących przestrzeni nazw można zaimportować:</span><span class="sxs-lookup"><span data-stu-id="c4f99-142">That the following namespaces be imported:</span></span>

  [!code-csharp[TimeZone2.Serialization#2](../../../samples/snippets/csharp/VS_Snippets_CLR/TimeZone2.Serialization/cs/SerializeTimeZoneData.cs#2)]
  [!code-vb[TimeZone2.Serialization#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/TimeZone2.Serialization/vb/SerializeTimeZoneData.vb#2)]

## <a name="see-also"></a><span data-ttu-id="c4f99-143">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="c4f99-143">See also</span></span>

* [<span data-ttu-id="c4f99-144">Daty, godziny i strefy czasowe</span><span class="sxs-lookup"><span data-stu-id="c4f99-144">Dates, times, and time zones</span></span>](../../../docs/standard/datetime/index.md)
* [<span data-ttu-id="c4f99-145">Strefy czasowe — omówienie</span><span class="sxs-lookup"><span data-stu-id="c4f99-145">Time zone overview</span></span>](../../../docs/standard/datetime/time-zone-overview.md)
* [<span data-ttu-id="c4f99-146">Instrukcje: Przywracanie stref czasowych z zasobu osadzonego</span><span class="sxs-lookup"><span data-stu-id="c4f99-146">How to: Restore time zones from an embedded resource</span></span>](../../../docs/standard/datetime/restore-time-zones-from-an-embedded-resource.md)

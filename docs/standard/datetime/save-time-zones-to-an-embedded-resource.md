---
title: 'Porady: zapisywanie stref czasowych w zasobie osadzonym'
ms.custom: 
ms.date: 04/10/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- time zones [.NET Framework], saving
- time zone objects [.NET Framework], serializing
- time zone objects [.NET Framework], saving
ms.assetid: 3c96d83a-a057-4496-abb0-8f4b12712558
caps.latest.revision: "12"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 96dd3f0a3ed27a9e09c62f3ad4f450ced5a8e644
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/18/2017
---
# <a name="how-to-save-time-zones-to-an-embedded-resource"></a><span data-ttu-id="a58b0-102">Porady: zapisywanie stref czasowych w zasobie osadzonym</span><span class="sxs-lookup"><span data-stu-id="a58b0-102">How to: Save time zones to an embedded resource</span></span>

<span data-ttu-id="a58b0-103">Strefa czasowa aplikacji z obsługą często wymaga obecności daną strefę czasową.</span><span class="sxs-lookup"><span data-stu-id="a58b0-103">A time zone-aware application often requires the presence of a particular time zone.</span></span> <span data-ttu-id="a58b0-104">Jednak ponieważ dostępność poszczególnych <xref:System.TimeZoneInfo> obiektów zależy od informacji przechowywanych w rejestrze systemu lokalnego, nawet zwyczajowo dostępnych stref czasowych nie może występować.</span><span class="sxs-lookup"><span data-stu-id="a58b0-104">However, because the availability of individual <xref:System.TimeZoneInfo> objects depends on information stored in the local system's registry, even customarily available time zones may be absent.</span></span> <span data-ttu-id="a58b0-105">Ponadto informacje o niestandardowych stref czasowych utworzone za pomocą <xref:System.TimeZoneInfo.CreateCustomTimeZone%2A> — metoda nie jest przechowywany z innych informacji o strefie czasowej w rejestrze.</span><span class="sxs-lookup"><span data-stu-id="a58b0-105">In addition, information about custom time zones instantiated by using the <xref:System.TimeZoneInfo.CreateCustomTimeZone%2A> method is not stored with other time zone information in the registry.</span></span> <span data-ttu-id="a58b0-106">W celu zapewnienia, że tych stref czasowych są dostępne, gdy są potrzebne, można je zapisać, szeregując je i je później przywrócić przez ich deserializacji.</span><span class="sxs-lookup"><span data-stu-id="a58b0-106">To ensure that these time zones are available when they are needed, you can save them by serializing them, and later restore them by deserializing them.</span></span>

<span data-ttu-id="a58b0-107">Zazwyczaj serializacji <xref:System.TimeZoneInfo> obiekt występuje oprócz aplikacji obsługujących strefę czasową.</span><span class="sxs-lookup"><span data-stu-id="a58b0-107">Typically, serializing a <xref:System.TimeZoneInfo> object occurs apart from the time zone-aware application.</span></span> <span data-ttu-id="a58b0-108">W zależności od magazyn danych używany do przechowywania serializacji <xref:System.TimeZoneInfo> obiekty, strefa czasowa danych może być serializowany jako część procedury lub instalacyjnego (na przykład, gdy dane są przechowywane w kluczu rejestru aplikacji) lub w ramach standardowego narzędzia, z systemem przed kompilowania aplikacji końcowego (na przykład, gdy dane serializowane są przechowywane w pliku .NET XML (resx) zasobów).</span><span class="sxs-lookup"><span data-stu-id="a58b0-108">Depending on the data store used to hold serialized <xref:System.TimeZoneInfo> objects, time zone data may be serialized as part of a setup or installation routine (for example, when the data is stored in an application key of the registry), or as part of a utility routine that runs before the final application is compiled (for example, when the serialized data is stored in a .NET XML resource (.resx) file).</span></span>

<span data-ttu-id="a58b0-109">Oprócz pliku zasobu, który jest kompilowany razem z aplikacją kilka innych magazynów danych może służyć do informacji o strefie czasowej.</span><span class="sxs-lookup"><span data-stu-id="a58b0-109">In addition to a resource file that is compiled with the application, several other data stores can be used for time zone information.</span></span> <span data-ttu-id="a58b0-110">Należą do nich między innymi:</span><span class="sxs-lookup"><span data-stu-id="a58b0-110">These include the following:</span></span>

* <span data-ttu-id="a58b0-111">Rejestr.</span><span class="sxs-lookup"><span data-stu-id="a58b0-111">The registry.</span></span> <span data-ttu-id="a58b0-112">Należy pamiętać, że aplikacja powinna podkluczy klucza własnej aplikacji do przechowywania danych niestandardowych strefy czasowej zamiast podkluczy HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Windows NT\CurrentVersion\Time strefy.</span><span class="sxs-lookup"><span data-stu-id="a58b0-112">Note that an application should use the subkeys of its own application key to store custom time zone data rather than using the subkeys of HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Windows NT\CurrentVersion\Time Zones.</span></span>

* <span data-ttu-id="a58b0-113">Pliki konfiguracji.</span><span class="sxs-lookup"><span data-stu-id="a58b0-113">Configuration files.</span></span>

* <span data-ttu-id="a58b0-114">Inne pliki systemowe.</span><span class="sxs-lookup"><span data-stu-id="a58b0-114">Other system files.</span></span>

### <a name="to-save-a-time-zone-by-serializing-it-to-a-resx-file"></a><span data-ttu-id="a58b0-115">Aby zapisać strefę czasową, szeregując go do pliku .resx</span><span class="sxs-lookup"><span data-stu-id="a58b0-115">To save a time zone by serializing it to a .resx file</span></span>

1. <span data-ttu-id="a58b0-116">Pobieranie istniejących strefę czasową lub tworzenia nowej strefy czasowej.</span><span class="sxs-lookup"><span data-stu-id="a58b0-116">Retrieve an existing time zone or create a new time zone.</span></span>

   <span data-ttu-id="a58b0-117">Można pobrać istniejący strefy czasowej, zobacz [jak: dostęp do wstępnie zdefiniowanych obiektów stref UTC i czasem lokalnym](../../../docs/standard/datetime/access-utc-and-local.md) i [porady: Tworzenie wystąpień obiektów TimeZoneInfo](../../../docs/standard/datetime/instantiate-time-zone-info.md).</span><span class="sxs-lookup"><span data-stu-id="a58b0-117">To retrieve an existing time zone, see [How to: Access the predefined UTC and local time zone objects](../../../docs/standard/datetime/access-utc-and-local.md) and [How to: Instantiate a TimeZoneInfo object](../../../docs/standard/datetime/instantiate-time-zone-info.md).</span></span>

   <span data-ttu-id="a58b0-118">Aby utworzyć nowej strefy czasowej, wywoływanie jednego z przeciążeń <xref:System.TimeZoneInfo.CreateCustomTimeZone%2A> metody.</span><span class="sxs-lookup"><span data-stu-id="a58b0-118">To create a new time zone, call one of the overloads of the <xref:System.TimeZoneInfo.CreateCustomTimeZone%2A> method.</span></span> <span data-ttu-id="a58b0-119">Aby uzyskać więcej informacji, zobacz [porady: tworzenie stref czasowych bez reguł korygowania](../../../docs/standard/datetime/create-time-zones-without-adjustment-rules.md) i [porady: tworzenie stref czasowych przy użyciu reguł korygowania](../../../docs/standard/datetime/create-time-zones-with-adjustment-rules.md).</span><span class="sxs-lookup"><span data-stu-id="a58b0-119">For more information, see [How to: Create time zones without adjustment rules](../../../docs/standard/datetime/create-time-zones-without-adjustment-rules.md) and [How to: Create time zones with adjustment rules](../../../docs/standard/datetime/create-time-zones-with-adjustment-rules.md).</span></span>

2. <span data-ttu-id="a58b0-120">Wywołanie <xref:System.TimeZoneInfo.ToSerializedString%2A> metodę w celu utworzenia ciąg, który zawiera dane strefy czasowej.</span><span class="sxs-lookup"><span data-stu-id="a58b0-120">Call the <xref:System.TimeZoneInfo.ToSerializedString%2A> method to create a string that contains the time zone's data.</span></span>

3. <span data-ttu-id="a58b0-121">Utwórz wystąpienie <xref:System.IO.StreamWriter> obiektu podając nazwę i opcjonalnie ścieżkę pliku .resx do <xref:System.IO.StreamWriter> konstruktora klasy.</span><span class="sxs-lookup"><span data-stu-id="a58b0-121">Instantiate a <xref:System.IO.StreamWriter> object by providing the name and optionally the path of the .resx file to the <xref:System.IO.StreamWriter> class constructor.</span></span>

4. <span data-ttu-id="a58b0-122">Utwórz wystąpienie <xref:System.Resources.ResXResourceWriter> obiektu przez przekazywanie <xref:System.IO.StreamWriter> do obiektu <xref:System.Resources.ResXResourceWriter> konstruktora klasy.</span><span class="sxs-lookup"><span data-stu-id="a58b0-122">Instantiate a <xref:System.Resources.ResXResourceWriter> object by passing the <xref:System.IO.StreamWriter> object to the <xref:System.Resources.ResXResourceWriter> class constructor.</span></span>

5. <span data-ttu-id="a58b0-123">Ciąg do serializacji przebiegu strefę czasową <xref:System.Resources.ResXResourceWriter.AddResource%2A?displayProperty=nameWithType> metody.</span><span class="sxs-lookup"><span data-stu-id="a58b0-123">Pass the time zone's serialized string to the <xref:System.Resources.ResXResourceWriter.AddResource%2A?displayProperty=nameWithType> method.</span></span>

6. <span data-ttu-id="a58b0-124">Wywołanie <xref:System.Resources.ResXResourceWriter.Generate%2A?displayProperty=nameWithType> metody.</span><span class="sxs-lookup"><span data-stu-id="a58b0-124">Call the <xref:System.Resources.ResXResourceWriter.Generate%2A?displayProperty=nameWithType> method.</span></span>

7. <span data-ttu-id="a58b0-125">Wywołanie <xref:System.Resources.ResXResourceWriter.Close%2A?displayProperty=nameWithType> metody.</span><span class="sxs-lookup"><span data-stu-id="a58b0-125">Call the <xref:System.Resources.ResXResourceWriter.Close%2A?displayProperty=nameWithType> method.</span></span>

8. <span data-ttu-id="a58b0-126">Zamknij <xref:System.IO.StreamWriter> obiektu przez wywołanie jego <xref:System.IO.StreamWriter.Close%2A> metody.</span><span class="sxs-lookup"><span data-stu-id="a58b0-126">Close the <xref:System.IO.StreamWriter> object by calling its <xref:System.IO.StreamWriter.Close%2A> method.</span></span>

9. <span data-ttu-id="a58b0-127">Dodaj plik .resx wygenerowanego do projektu programu Visual Studio aplikacji.</span><span class="sxs-lookup"><span data-stu-id="a58b0-127">Add the generated .resx file to the application's Visual Studio project.</span></span>

10. <span data-ttu-id="a58b0-128">Przy użyciu **właściwości** okna w programie Visual Studio, upewnij się, że plik .resx **Akcja kompilacji** właściwość jest ustawiona na **osadzonego zasobu**.</span><span class="sxs-lookup"><span data-stu-id="a58b0-128">Using the **Properties** window in Visual Studio, make sure that the .resx file's **Build Action** property is set to **Embedded Resource**.</span></span>

## <a name="example"></a><span data-ttu-id="a58b0-129">Przykład</span><span class="sxs-lookup"><span data-stu-id="a58b0-129">Example</span></span>

<span data-ttu-id="a58b0-130">Poniższy przykład serializuje <xref:System.TimeZoneInfo> obiekt, który reprezentuje Środkowa (czas standardowy) i <xref:System.TimeZoneInfo> obiekt reprezentujący Palmer stacji, czas Antarktyka plik zasobu .NET XML o nazwie SerializedTimeZones.resx.</span><span class="sxs-lookup"><span data-stu-id="a58b0-130">The following example serializes a <xref:System.TimeZoneInfo> object that represents Central Standard Time and a <xref:System.TimeZoneInfo> object that represents the Palmer Station, Antarctica time to a .NET XML resource file that is named SerializedTimeZones.resx.</span></span> <span data-ttu-id="a58b0-131">Środkowy czas stand. zwykle jest zdefiniowana w rejestrze. Palmer stacji, Antarktyka jest niestandardowa strefa czasowa.</span><span class="sxs-lookup"><span data-stu-id="a58b0-131">Central Standard Time is typically defined in the registry; Palmer Station, Antarctica is a custom time zone.</span></span>

[!code-csharp[TimeZone2.Serialization#1](../../../samples/snippets/csharp/VS_Snippets_CLR/TimeZone2.Serialization/cs/SerializeTimeZoneData.cs#1)]
[!code-vb[TimeZone2.Serialization#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/TimeZone2.Serialization/vb/SerializeTimeZoneData.vb#1)]

<span data-ttu-id="a58b0-132">W tym przykładzie serializuje <xref:System.TimeZoneInfo> obiektów, tak aby były dostępne w pliku zasobów w czasie kompilacji.</span><span class="sxs-lookup"><span data-stu-id="a58b0-132">This example serializes <xref:System.TimeZoneInfo> objects so that they are available in a resource file at compile time.</span></span>

<span data-ttu-id="a58b0-133">Ponieważ <xref:System.Resources.ResXResourceWriter.Generate%2A?displayProperty=nameWithType> metoda dodaje informacje o nagłówku pełną plik zasobu .NET XML, nie można dodać zasoby do istniejącego pliku.</span><span class="sxs-lookup"><span data-stu-id="a58b0-133">Because the <xref:System.Resources.ResXResourceWriter.Generate%2A?displayProperty=nameWithType> method adds complete header information to a .NET XML resource file, it cannot be used to add resources to an existing file.</span></span> <span data-ttu-id="a58b0-134">Przykład obsługi to przez sprawdzanie pliku SerializedTimeZones.resx i, jeśli istnieje, przechowywania wszystkich jej zasobów innych niż dwa serializować stref czasowych do ogólnego <xref:System.Collections.Generic.Dictionary%602> obiektu.</span><span class="sxs-lookup"><span data-stu-id="a58b0-134">The example handles this by checking for the SerializedTimeZones.resx file and, if it exists, storing all of its resources other than the two serialized time zones to a generic <xref:System.Collections.Generic.Dictionary%602> object.</span></span> <span data-ttu-id="a58b0-135">Istniejący plik jest usuwany, a istniejące zasoby zostaną dodane do nowego pliku SerializedTimeZones.resx.</span><span class="sxs-lookup"><span data-stu-id="a58b0-135">The existing file is then deleted and the existing resources are added to a new SerializedTimeZones.resx file.</span></span> <span data-ttu-id="a58b0-136">Dane serializowane strefa czasowa jest także dodawane do tego pliku.</span><span class="sxs-lookup"><span data-stu-id="a58b0-136">The serialized time zone data is also added to this file.</span></span>

<span data-ttu-id="a58b0-137">Klucz (lub **nazwa**) pól zasobów nie może zawierać spacji osadzonych.</span><span class="sxs-lookup"><span data-stu-id="a58b0-137">The key (or **Name**) fields of resources should not contain embedded spaces.</span></span> <span data-ttu-id="a58b0-138"><xref:System.String.Replace%28System.String%2CSystem.String%29> Metoda jest wywoływana przed są przypisane do pliku zasobów, Usuń wszystkie spacje w identyfikatorach strefy czasowej.</span><span class="sxs-lookup"><span data-stu-id="a58b0-138">The <xref:System.String.Replace%28System.String%2CSystem.String%29> method is called to remove all embedded spaces in the time zone identifiers before they are assigned to the resource file.</span></span>

## <a name="compiling-the-code"></a><span data-ttu-id="a58b0-139">Kompilowanie kodu</span><span class="sxs-lookup"><span data-stu-id="a58b0-139">Compiling the code</span></span>

<span data-ttu-id="a58b0-140">Ten przykład wymaga:</span><span class="sxs-lookup"><span data-stu-id="a58b0-140">This example requires:</span></span>

* <span data-ttu-id="a58b0-141">Odwołanie do System.Windows.Forms.dll i System.Core.dll dodania do projektu.</span><span class="sxs-lookup"><span data-stu-id="a58b0-141">That a reference to System.Windows.Forms.dll and System.Core.dll be added to the project.</span></span>

* <span data-ttu-id="a58b0-142">Czy następujących przestrzeni nazw można importować:</span><span class="sxs-lookup"><span data-stu-id="a58b0-142">That the following namespaces be imported:</span></span>

  [!code-csharp[TimeZone2.Serialization#2](../../../samples/snippets/csharp/VS_Snippets_CLR/TimeZone2.Serialization/cs/SerializeTimeZoneData.cs#2)]
  [!code-vb[TimeZone2.Serialization#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/TimeZone2.Serialization/vb/SerializeTimeZoneData.vb#2)]

## <a name="see-also"></a><span data-ttu-id="a58b0-143">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="a58b0-143">See also</span></span>

<span data-ttu-id="a58b0-144">[Daty, godziny i strefy czasowe](../../../docs/standard/datetime/index.md)
[Przegląd stref czasowych](../../../docs/standard/datetime/time-zone-overview.md)
[porady: Przywracanie stref czasowych z zasobu osadzonego](../../../docs/standard/datetime/restore-time-zones-from-an-embedded-resource.md)</span><span class="sxs-lookup"><span data-stu-id="a58b0-144">[Dates, times, and time zones](../../../docs/standard/datetime/index.md)
[Time zone overview](../../../docs/standard/datetime/time-zone-overview.md)
[How to: Restore time zones from an embedded resource](../../../docs/standard/datetime/restore-time-zones-from-an-embedded-resource.md)</span></span>

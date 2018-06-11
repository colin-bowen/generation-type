# generation-type
string analysis to see what type of generation is created by each node

%call filename
filename = "SpanishPortuguese_400kV_Location_PowerGrid";

%call generation name
generation = "Generación";
[~,generation_name] = xlsread(filename, generation, "A2:A113");
[~,generation_fuel] = xlsread(filename, generation, "F2:F113");


%look for gen type e.g. nuclear, ccgt, hydro in string analysis

%first define gen types
gen_hydro = "Hydro";
gen_CCGT = "CCGT";
gen_Coal = "Coal";
gen_OCGT = "OCGT";
gen_Thermal = "Thermal";
gen_Nuclear = "Nuclear";
gen_GICC = "GICC"; %the same as CCGT

% define fuel types
fuel_Hydro = "Hydro";
fuel_Coal = "Coal";
fuel_Natgas = "Natural Gas";
fuel_Oil = "Fuel Oil";
fuel_Nuclear = "Nuclear";
fuel_Lignite = "Lignite";
fuel_Unknown = "Unknown";

%is the unit shut down
shutdown = "Shutdown"

%sort generators by generation type
type_CCGT = zeros(length(generation_name),1);
for i = 1:length(generation_name)
  type_CCGT(i) = strfind(generation_name(i), gen_CCGT)
  if type_CCGT(i) ~= 0 %will select those not equal to zero and put that into the index of CCGTs
    index_CCGT(i) = i;
  end
end

type_Hydro = zeros(length(generation_name),1);
for i = 1:length(generation_name)
  type_Hydro(i) = strfind(generation_name(i), gen_Hydro)
  if type_Hydro(i) ~= 0 %will select those not equal to zero and put that into the index of Hydros
    index_Hydro(i) = i;
  end
end

type_Coal = zeros(length(generation_name),1);
for i = 1:length(generation_name)
  type_Coal(i) = strfind(generation_name(i), gen_Coal)
  if type_Coal(i) ~= 0 %will select those not equal to zero and put that into the index of Coals
    index_Coal(i) = i;
  end
end

type_OCGT = zeros(length(generation_name),1);
for i = 1:length(generation_name)
  type_OCGT(i) = strfind(generation_name(i), gen_OCGT)
  if type_OCGT(i) ~= 0 %will select those not equal to zero and put that into the index of OCGTs
    index_OCGT(i) = i;
  end
end

type_Thermal = zeros(length(generation_name),1);
for i = 1:length(generation_name)
  type_Thermal(i) = strfind(generation_name(i), gen_Thermal)
  if type_Thermal(i) ~= 0 %will select those not equal to zero and put that into the index of Thermals
    index_Thermal(i) = i;
  end
end

type_Nuclear = zeros(length(generation_name),1);
for i = 1:length(generation_name)
  type_Nuclear(i) = strfind(generation_name(i), gen_Nuclear)
  if type_Nuclear(i) ~= 0 %will select those not equal to zero and put that into the index of Nuclears
    index_Nuclear(i) = i;
  end
end


type_GICC = zeros(length(generation_name),1);
for i = 1:length(generation_name)
  type_GICC(i) = strfind(generation_name(i), gen_GICC)
  if type_GICC(i) ~= 0 %will select those not equal to zero and put that into the index of GICCs
    index_GICC(i) = i;
  end
end

%merge GICC and CCGT

index_CCGT = [index_CCGT; index_GICC];


%sort generators by fuel type
fueltype_Hydro = zeros(length(generation_fuel),1);
for i = 1:length(generation_fuel)
  fueltype_Hydro(i) = strfind(generation_fuel(i), fuel_Hydro);
  if fueltype_Hydro(i) ~= 0 %will select those not equal to zero and put that into the index of Hydros
    fuelindex_Hydro(i) = i;
  end
end


fueltype_Hydro = zeros(length(generation_fuel),1);
for i = 1:length(generation_fuel)
  fueltype_Hydro(i) = strfind(generation_fuel(i), fuel_Hydro);
  if fueltype_Hydro(i) ~= 0 %will select those not equal to zero and put that into the index of Hydros
    fuelindex_Hydro(i) = i;
  end
end

fueltype_Natgas = zeros(length(generation_fuel),1);
for i = 1:length(generation_fuel)
  fueltype_Natgas(i) = strfind(generation_fuel(i), fuel_Natgas)
  if fueltype_Natgas(i) ~= 0 %will select those not equal to zero and put that into the index of Natgas
    fuelindex_Natgas(i) = i;
  end
end


fueltype_Coal = zeros(length(generation_fuel),1);
for i = 1:length(generation_fuel)
  fueltype_Coal(i) = strfind(generation_fuel(i), fuel_Coal);
  if fueltype_Coal(i) ~= 0 %will select those not equal to zero and put that into the index of Coals
    fuelindex_Coal(i) = i;
  end
end


fueltype_OCGT = zeros(length(generation_fuel),1);
for i = 1:length(generation_fuel)
  fueltype_OCGT(i) = strfind(generation_fuel(i), fuel_OCGT);
  if fueltype_OCGT(i) ~= 0 %will select those not equal to zero and put that into the index of OCGTs
    fuelindex_OCGT(i) = i;
  end
end

fueltype_Oil = zeros(length(generation_fuel),1);
for i = 1:length(generation_fuel)
  fueltype_Oil(i) = strfind(generation_fuel(i), fuel_Oil);
  if fueltype_Oil(i) ~= 0 %will select those not equal to zero and put that into the index of Oils
    fuelindex_Oil(i) = i;
  end
end

fueltype_Nuclear = zeros(length(generation_fuel),1);
for i = 1:length(generation_fuel)
  fueltype_Nuclear(i) = strfind(generation_fuel(i), fuel_Nuclear);
  if fueltype_Nuclear(i) ~= 0 %will select those not equal to zero and put that into the index of Hydros
    fuelindex_Nuclear(i) = i;
  end
end

fueltype_Lignite = zeros(length(generation_fuel),1);
for i = 1:length(generation_fuel)
  fueltype_Lignite(i) = strfind(generation_fuel(i), fuel_Lignite)
  if fueltype_Lignite(i) ~= 0 %will select those not equal to zero and put that into the index of Lignites
    fuelindex_Lignite(i) = i;
  end
end

fueltype_Unknown = zeros(length(generation_fuel),1);
for i = 1:length(generation_fuel)
  fueltype_Unknown(i) = strfind(generation_fuel(i), fuel_Lignite)
  if fueltype_Unknown(i) ~= 0 %will select those not equal to zero and put that into the index of Unknowns
    fuelindex_Unknown(i) = i;
  end
end



%get rid of shut down generators
%probably easier to do manually

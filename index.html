import React, { useMemo, useState } from 'react';

function shuffleArray(array) {
  const copy = [...array];
  for (let i = copy.length - 1; i > 0; i -= 1) {
    const j = Math.floor(Math.random() * (i + 1));
    [copy[i], copy[j]] = [copy[j], copy[i]];
  }
  return copy;
}

const clamp = (value, min = 0, max = 100) => Math.max(min, Math.min(max, value));

function makeInitialGame() {
  return {
    day: 1,
    phase: 'briefing',
    sanitation: 52,
    supplies: 62,
    staff: 55,
    morale: 68,
    knowledge: 28,
    transport: 40,
    patients: {
      disease: 30,
      wounded: 18,
      contagious: 10,
      recovering: 12,
    },
    diseaseBreakdown: {
      dysentery: 12,
      typhoid: 8,
      malaria: 7,
      pneumonia: 6,
      smallpox: 5,
      measles: 4,
    },
    survivors: 0,
    deaths: 0,
    reputation: 0,
    streak: 0,
    log: [
      'Day 1: Your Civil War hospital opens during a surge of disease, infection, and battlefield injuries.',
    ],
    learned: [
      'Disease killed more soldiers than battle wounds during the Civil War. Your job is to manage a whole medical system, not just click the surgery button.',
    ],
    upgrades: {
      pavilion: false,
      ambulance: false,
      isolation: false,
      supplyDepot: false,
      recordkeeping: false,
      cleanWater: false,
      nursingRotation: false,
      pharmacy: false,
    },
  };
}

const diseaseIcons = {
  dysentery: '🤢',
  typhoid: '🥵',
  malaria: '🦟',
  pneumonia: '🫁',
  smallpox: '🧬',
  measles: '🔴',
};

const historicalCards = [
  {
    title: 'Disease Is the Main Enemy',
    icon: '🦠',
    text: 'Civil War camps were crowded and often unsanitary, which allowed dysentery, typhoid, pneumonia, malaria, measles, and smallpox to spread faster than armies could control them.',
  },
  {
    title: 'Germ Theory Was Not Widely Accepted',
    icon: '🔬',
    text: 'Many physicians did not yet understand that microorganisms caused disease. They often focused on foul smells and airflow instead of sterilizing tools properly.',
  },
  {
    title: 'Amputation Could Save Lives',
    icon: '🩹',
    text: 'Minié balls shattered bones and destroyed tissue. Early amputation could prevent infection from spreading, while delayed surgery was much riskier.',
  },
  {
    title: 'Organization Changed Medicine',
    icon: '🚑',
    text: 'Ambulance corps, triage, pavilion hospitals, transportation by train or boat, and organized supply systems helped Civil War medicine become more systematic over time.',
  },
  {
    title: 'Nursing Was a System',
    icon: '🧑‍⚕️',
    text: 'Nurses and relief workers improved patient care through food, comfort, cleaning, supplies, and organization. Survival depended on more than surgeons alone.',
  },
];

const eventTemplates = [
  {
    title: 'Contaminated Water Near Camp',
    icon: '💧',
    type: 'Disease Outbreak',
    scene: 'A line of soldiers reports severe diarrhea, weakness, and dehydration. The water barrels near camp smell foul, but the hospital is already overloaded.',
    sourceIdea: 'Dysentery and typhoid often spread through contaminated food and water in unsanitary camps.',
    options: [
      {
        label: 'Move waste pits farther from camp and boil water',
        quality: 3,
        effects: { sanitation: +18, supplies: -9, staff: -6, morale: +4, disease: -13, survivors: +5, knowledge: +3 },
        feedback: 'Strong choice. Sanitation directly reduces disease spread. Even without modern germ theory, cleaner water and better waste disposal could save lives.',
      },
      {
        label: 'Treat only the sickest patients with available medicine',
        quality: 2,
        effects: { supplies: -14, disease: -7, survivors: +6, morale: -3 },
        feedback: 'Mixed choice. This helps some patients, but it does not fix the contaminated water source, so disease pressure remains.',
      },
      {
        label: 'Ignore the water and focus on battle wounds',
        quality: 1,
        effects: { sanitation: -12, disease: +18, contagious: +6, deaths: +7, morale: -9 },
        feedback: 'Dangerous. Civil War hospitals could not survive by treating wounds alone because disease was the leading killer.',
      },
    ],
  },
  {
    title: 'Foul-Smelling Ward',
    icon: '🪟',
    type: 'Medical Knowledge',
    scene: 'A ward smells terrible. Some doctors argue the bad air itself is causing illness, while others want the room cleaned and patients separated.',
    sourceIdea: 'Many Civil War doctors believed in miasma theory, but ventilation and cleaning sometimes still helped reduce disease.',
    options: [
      {
        label: 'Open windows, clean bedding, and separate the sickest patients',
        quality: 3,
        effects: { sanitation: +14, staff: -6, contagious: -8, recovering: +5, knowledge: +4, survivors: +4 },
        feedback: 'Excellent. Even if doctors misunderstood germs, ventilation, cleaning, and separation could still reduce outbreaks.',
      },
      {
        label: 'Only mask the smell with lime and odor control',
        quality: 2,
        effects: { sanitation: +5, supplies: -5, knowledge: +1, contagious: +2 },
        feedback: 'Partly helpful, but incomplete. Odor control fit miasma theory, but it did not fully address infection or contamination.',
      },
      {
        label: 'Keep all patients together to save space',
        quality: 1,
        effects: { contagious: +12, disease: +9, deaths: +6, morale: -8 },
        feedback: 'Bad outcome. Overcrowding made contagious disease spread through hospitals and camps much faster.',
      },
    ],
  },
  {
    title: 'Shattered Bone Injury',
    icon: '🦴',
    type: 'Surgery Decision',
    scene: 'A soldier arrives with a leg wound from a Minié ball. The bone is shattered. You must decide before infection spreads.',
    sourceIdea: 'Primary amputations performed soon after injury had better survival chances than secondary amputations after infection developed.',
    options: [
      {
        label: 'Perform immediate primary amputation with anesthesia',
        quality: 3,
        effects: { supplies: -16, wounded: -8, survivors: +7, deaths: +1, morale: -4, knowledge: +4 },
        feedback: 'Historically strong choice. Severe limb injuries often could not be repaired, and early amputation could prevent fatal infection.',
      },
      {
        label: 'Wait and try to save the limb',
        quality: 1,
        effects: { wounded: +2, deaths: +8, morale: -6, knowledge: +2 },
        feedback: 'Risky. Without antibiotics or modern infection control, waiting often allowed infection to spread before surgery.',
      },
      {
        label: 'Use supplies on less severe wounds instead',
        quality: 2,
        effects: { supplies: -7, wounded: -5, survivors: +4, deaths: +4 },
        feedback: 'Mixed triage. This saves some patients, but the soldier with the shattered bone becomes much less likely to survive.',
      },
    ],
  },
  {
    title: 'Overcrowded Hospital Ward',
    icon: '🏥',
    type: 'Hospital Design',
    scene: 'Every bed is full. More patients are arriving from the battlefield, and contagious patients are lying beside recovering surgical patients.',
    sourceIdea: 'Pavilion-style hospitals used airflow, spacing, and separation to improve hospital organization.',
    options: [
      {
        label: 'Create separated wards and improve airflow',
        quality: 3,
        effects: { supplies: -10, staff: -8, sanitation: +16, contagious: -10, recovering: +8, survivors: +5, knowledge: +4 },
        feedback: 'Great systems thinking. Separation and ventilation helped hospitals manage disease even before modern germ theory.',
      },
      {
        label: 'Discharge stable patients by train or boat',
        quality: 2,
        effects: { transport: -8, recovering: -7, survivors: +7, morale: +3, supplies: -5 },
        feedback: 'Good logistics, but it does not solve the ward design problem by itself. It reduces crowding for now.',
      },
      {
        label: 'Keep everyone in the same ward',
        quality: 1,
        effects: { contagious: +10, disease: +8, recovering: -4, deaths: +5, morale: -6 },
        feedback: 'Overcrowding increases disease spread and makes recovery harder.',
      },
    ],
  },
  {
    title: 'Supplies Arrive from Clara Barton',
    icon: '📦',
    type: 'Relief Work',
    scene: 'A volunteer relief worker arrives with food, bandages, and comfort items for wounded soldiers. You must decide how to use them.',
    sourceIdea: 'Clara Barton organized supplies, brought aid to battlefronts, comforted the wounded, and later helped missing soldiers’ families.',
    options: [
      {
        label: 'Use supplies for surgery, food, and clean bedding',
        quality: 3,
        effects: { supplies: +16, morale: +10, sanitation: +6, survivors: +5, recovering: +5 },
        feedback: 'Strong choice. Civil War medicine depended on logistics, not only doctors. Supplies could improve survival and morale.',
      },
      {
        label: 'Save everything for future emergencies',
        quality: 2,
        effects: { supplies: +24, morale: -5, disease: +3 },
        feedback: 'Conservative, but not always best. Hoarding supplies while patients deteriorate can cost lives.',
      },
      {
        label: 'Use supplies only on officers',
        quality: 1,
        effects: { morale: -15, survivors: +2, deaths: +4, reputation: -5 },
        feedback: 'Unfair treatment damages morale and does not manage the hospital as a whole system.',
      },
    ],
  },
  {
    title: 'Smallpox Threat',
    icon: '💉',
    type: 'Prevention',
    scene: 'A suspected smallpox case appears in camp. Some soldiers have never been exposed before, and panic spreads through the hospital.',
    sourceIdea: 'Vaccination was sometimes used to reduce smallpox outbreaks during the war.',
    options: [
      {
        label: 'Vaccinate exposed soldiers and isolate suspected cases',
        quality: 3,
        effects: { supplies: -12, staff: -5, contagious: -14, morale: +5, survivors: +6, knowledge: +4 },
        feedback: 'Excellent prevention strategy. Smallpox was one disease where vaccination could help reduce spread.',
      },
      {
        label: 'Only isolate the visible case',
        quality: 2,
        effects: { contagious: -5, morale: +1, disease: +3 },
        feedback: 'Somewhat helpful, but exposed soldiers may still spread disease before obvious symptoms appear.',
      },
      {
        label: 'Assume it is just a rash',
        quality: 1,
        effects: { contagious: +18, disease: +10, deaths: +8, morale: -12 },
        feedback: 'Very dangerous. Crowded camps made contagious diseases spread rapidly when ignored.',
      },
    ],
  },
  {
    title: 'Malaria in the Lowlands',
    icon: '🦟',
    type: 'Medicine Allocation',
    scene: 'Fever cases rise near swampy ground. You have a limited amount of quinine, but other patients also need supplies.',
    sourceIdea: 'Quinine was one of the few medicines commonly used for malaria during the Civil War.',
    options: [
      {
        label: 'Use quinine on malaria cases and move tents away from swampy ground',
        quality: 3,
        effects: { supplies: -12, staff: -4, disease: -10, morale: +6, survivors: +5, knowledge: +3 },
        feedback: 'Good. You combined treatment with prevention by reducing exposure and using the medicine where it was most relevant.',
      },
      {
        label: 'Use quinine on every fever case',
        quality: 2,
        effects: { supplies: -20, disease: -4, morale: +2 },
        feedback: 'Not efficient. Quinine was useful for malaria, but not every fever had the same cause.',
      },
      {
        label: 'Save quinine for later',
        quality: 1,
        effects: { supplies: +2, disease: +9, deaths: +4, morale: -5 },
        feedback: 'Delaying treatment allows malaria cases to weaken the army and overwhelm the hospital.',
      },
    ],
  },
  {
    title: 'Missing Patient Records',
    icon: '📋',
    type: 'Organization',
    scene: 'Doctors are losing track of who was treated, who needs surgery, and who was transported. Families are asking for missing soldiers.',
    sourceIdea: 'Civil War medical systems became more organized over time through records, hospital systems, transportation, and relief work.',
    options: [
      {
        label: 'Assign staff to patient records and treatment tracking',
        quality: 3,
        effects: { staff: -7, knowledge: +10, morale: +4, survivors: +4, reputation: +6 },
        feedback: 'Great long-term choice. Recordkeeping helps doctors track outcomes, organize patients, and learn from repeated cases.',
      },
      {
        label: 'Focus all staff on immediate treatment only',
        quality: 2,
        effects: { wounded: -6, survivors: +5, knowledge: -2, reputation: -4 },
        feedback: 'This helps today, but poor organization makes future care less effective.',
      },
      {
        label: 'Ignore records until after the battle',
        quality: 1,
        effects: { morale: -8, reputation: -8, knowledge: -4, deaths: +3 },
        feedback: 'Bad systems outcome. In mass casualty settings, organization itself can become life-saving.',
      },
    ],
  },
  {
    title: 'Laudable Pus Misunderstanding',
    icon: '🧫',
    type: 'Infection Theory',
    scene: 'A surgeon believes pus in a wound is a sign of healing. Several wounds look swollen and smell foul, but the staff disagrees about whether this is dangerous.',
    sourceIdea: 'Some Civil War doctors saw pus as a positive sign even though it could indicate serious infection.',
    options: [
      {
        label: 'Treat pus as a warning sign and clean the wound area as much as possible',
        quality: 3,
        effects: { supplies: -10, staff: -4, wounded: -5, survivors: +5, knowledge: +6, sanitation: +4 },
        feedback: 'Strong choice. Even without full germ theory, recognizing infection risk and cleaning wounds improves survival.',
      },
      {
        label: 'Assume pus means healing and leave the wound alone',
        quality: 1,
        effects: { wounded: +5, deaths: +7, morale: -8, knowledge: -2 },
        feedback: 'Dangerous. This reflects the historical misunderstanding of “laudable pus,” which could hide fatal infection.',
      },
      {
        label: 'Use supplies only on soldiers who are still able to walk',
        quality: 2,
        effects: { supplies: -5, survivors: +2, wounded: +3, morale: -5 },
        feedback: 'This helps a few stable soldiers but abandons patients who may still be saved with better infection care.',
      },
    ],
  },
  {
    title: 'Heroic Medicine Debate',
    icon: '⚗️',
    type: 'Treatment Methods',
    scene: 'A feverish soldier is weakening. One doctor recommends purging and bloodletting, while another argues for rest, food, hydration, and observation.',
    sourceIdea: 'Heroic medicine used aggressive treatments such as bloodletting, purging, and blistering, which often weakened patients.',
    options: [
      {
        label: 'Use aggressive bloodletting and purging to rebalance the body',
        quality: 1,
        effects: { disease: +4, deaths: +5, morale: -7, knowledge: -2 },
        feedback: 'Bad outcome. Heroic treatments often weakened already sick patients instead of curing disease.',
      },
      {
        label: 'Give rest, hydration, food, and monitor symptoms',
        quality: 3,
        effects: { supplies: -8, disease: -5, recovering: +7, survivors: +4, knowledge: +4 },
        feedback: 'Better choice. Supportive care often mattered more than aggressive treatments that drained patients’ strength.',
      },
      {
        label: 'Do nothing until the fever becomes more severe',
        quality: 2,
        effects: { supplies: +2, disease: +7, morale: -3, deaths: +2 },
        feedback: 'Waiting saves supplies in the moment, but disease can worsen quickly in crowded camps.',
      },
    ],
  },
  {
    title: 'Hospital Laundry Crisis',
    icon: '🧺',
    type: 'Hospital Operations',
    scene: 'Bandages, sheets, and clothing are soiled. The hospital has a laundry area, but assigning workers there means fewer hands for immediate care.',
    sourceIdea: 'Organized hospitals often included laundries, kitchens, pharmacies, and storage buildings to support patient care.',
    options: [
      {
        label: 'Assign staff to laundry and clean bedding rotation',
        quality: 3,
        effects: { staff: -6, sanitation: +15, contagious: -5, recovering: +5, survivors: +3, knowledge: +3 },
        feedback: 'Strong systems choice. Clean bedding and clothing help reduce spread and improve recovery conditions.',
      },
      {
        label: 'Use all staff for surgery and ignore laundry for now',
        quality: 2,
        effects: { wounded: -5, survivors: +4, sanitation: -10, contagious: +5 },
        feedback: 'This saves some wounded patients immediately but worsens hospital conditions and disease spread.',
      },
      {
        label: 'Reuse dirty bandages to conserve supplies',
        quality: 1,
        effects: { supplies: +4, sanitation: -12, wounded: +7, deaths: +4 },
        feedback: 'Very risky. Reusing dirty materials increases infection danger in a hospital already fighting disease.',
      },
    ],
  },
  {
    title: 'Train Transport Choice',
    icon: '🚂',
    type: 'Transportation',
    scene: 'A train can move stable patients to a larger hospital, but the trip will use staff time and supplies. The field hospital is nearly full.',
    sourceIdea: 'Stable patients were sometimes transported by train or boat to larger hospitals farther from battlefields.',
    options: [
      {
        label: 'Send stable recovering patients to the larger hospital',
        quality: 3,
        effects: { supplies: -8, transport: -6, recovering: -8, survivors: +8, morale: +4, sanitation: +5 },
        feedback: 'Excellent logistics. Moving stable patients reduces overcrowding and improves chances for continued recovery.',
      },
      {
        label: 'Keep everyone nearby so doctors can watch them',
        quality: 2,
        effects: { morale: +1, sanitation: -7, contagious: +4, disease: +4 },
        feedback: 'Understandable, but overcrowding makes disease and infection harder to control.',
      },
      {
        label: 'Send the sickest contagious patients on the train with everyone else',
        quality: 1,
        effects: { transport: -8, contagious: +9, deaths: +5, reputation: -5 },
        feedback: 'Bad choice. Moving contagious patients without separation can spread disease beyond the hospital.',
      },
    ],
  },
  {
    title: 'Nurse Staffing Conflict',
    icon: '🧑‍⚕️',
    type: 'Nursing Care',
    scene: 'Nurses are exhausted. Some officers want them only assisting surgeons, but patients also need food, comfort, cleaning, and wound care.',
    sourceIdea: 'Nurses and hospital workers maintained hygiene, food, supplies, and patient comfort, not just surgical assistance.',
    options: [
      {
        label: 'Split nurses between surgery support and daily patient care',
        quality: 3,
        effects: { staff: -5, morale: +9, recovering: +6, sanitation: +5, survivors: +4 },
        feedback: 'Balanced and historically smart. Nursing care improved survival through hygiene, nutrition, comfort, and organization.',
      },
      {
        label: 'Put every nurse in surgery support',
        quality: 2,
        effects: { wounded: -7, survivors: +4, morale: -5, sanitation: -5, recovering: -2 },
        feedback: 'This helps surgery but neglects the broader care system that patients need to recover.',
      },
      {
        label: 'Dismiss nursing work as less important than surgery',
        quality: 1,
        effects: { morale: -12, sanitation: -10, recovering: -5, deaths: +4 },
        feedback: 'Bad systems decision. Civil War care depended heavily on nurses, supplies, cleanliness, and comfort.',
      },
    ],
  },
  {
    title: 'Medical Supply Triage',
    icon: '⚖️',
    type: 'Resource Allocation',
    scene: 'You have limited chloroform, bandages, quinine, food, and clean clothing. Every ward is asking for help at once.',
    sourceIdea: 'Civil War hospitals had to manage limited supplies across disease treatment, surgery, sanitation, and recovery.',
    options: [
      {
        label: 'Divide supplies by urgency: quinine to malaria, bandages to wounds, food to recovering patients',
        quality: 3,
        effects: { supplies: -18, disease: -6, wounded: -5, recovering: +6, survivors: +7, knowledge: +5 },
        feedback: 'Excellent triage. Matching supplies to the right medical problem makes scarce resources more effective.',
      },
      {
        label: 'Spend everything on surgery because it looks most dramatic',
        quality: 2,
        effects: { supplies: -22, wounded: -9, survivors: +5, disease: +8, morale: -4 },
        feedback: 'Surgery matters, but disease was often the larger threat. Ignoring illness lets the crisis grow.',
      },
      {
        label: 'Store supplies until conditions become desperate',
        quality: 1,
        effects: { supplies: +5, deaths: +6, disease: +7, wounded: +4, morale: -9 },
        feedback: 'Hoarding supplies during an active crisis causes preventable deaths.',
      },
    ],
  },
  {
    title: 'Sanitary Inspection Report',
    icon: '📑',
    type: 'Public Health',
    scene: 'Inspectors report dirty kitchens, waste near tents, and crowded sleeping areas. Fixing all of it will slow the hospital today.',
    sourceIdea: 'Sanitary efforts focused on hygiene, nutrition, camp inspection, clean clothing, and disease prevention.',
    options: [
      {
        label: 'Follow the inspection report and reorganize camp sanitation',
        quality: 3,
        effects: { staff: -8, supplies: -8, sanitation: +22, disease: -8, morale: +5, knowledge: +4 },
        feedback: 'Strong long-term choice. Public health efforts prevented disease from weakening the army.',
      },
      {
        label: 'Fix only the kitchen because food affects morale fastest',
        quality: 2,
        effects: { supplies: -5, sanitation: +7, morale: +6, disease: +2 },
        feedback: 'Partly useful, but disease prevention requires the whole camp environment, not just food.',
      },
      {
        label: 'Reject the report because surgeons need all resources',
        quality: 1,
        effects: { sanitation: -12, disease: +12, contagious: +5, deaths: +5 },
        feedback: 'Bad outcome. Ignoring public health lets disease do more damage than combat wounds.',
      },
    ],
  },
  {
    title: 'Kitchen and Diet Problem',
    icon: '🥣',
    type: 'Nutrition',
    scene: 'Recovering soldiers are weak. The kitchen can prepare better meals, but it will consume supplies and staff time.',
    sourceIdea: 'Diet and nutrition were part of disease prevention because weak soldiers were less able to recover from illness.',
    options: [
      {
        label: 'Improve meals for recovering and sick soldiers',
        quality: 3,
        effects: { supplies: -10, staff: -4, morale: +9, recovering: +8, survivors: +5, disease: -3 },
        feedback: 'Strong choice. Better nutrition improves recovery and reduces vulnerability to disease.',
      },
      {
        label: 'Feed only soldiers returning to battle fastest',
        quality: 2,
        effects: { supplies: -5, morale: -3, survivors: +3, recovering: -2, reputation: -3 },
        feedback: 'This has short-term military logic, but it ignores the hospital’s full recovery system.',
      },
      {
        label: 'Cut rations to save supplies',
        quality: 1,
        effects: { supplies: +8, morale: -12, disease: +8, deaths: +5 },
        feedback: 'Dangerous. Poor diet weakens patients and makes disease more deadly.',
      },
    ],
  },
  {
    title: 'Surgery Tent Overload',
    icon: '⛺',
    type: 'Mass Casualty Triage',
    scene: 'After a battle, wounded soldiers arrive faster than surgeons can operate. Some need immediate surgery; others can wait.',
    sourceIdea: 'Triage became essential when doctors had to prioritize patients with limited time, staff, and supplies.',
    options: [
      {
        label: 'Prioritize patients most likely to survive with immediate care',
        quality: 3,
        effects: { staff: -8, supplies: -15, wounded: -10, survivors: +9, knowledge: +5, morale: -2 },
        feedback: 'Strong triage. It is emotionally difficult but uses limited resources where they can save the most lives.',
      },
      {
        label: 'Treat patients in the order they arrive',
        quality: 2,
        effects: { supplies: -14, wounded: -5, survivors: +4, deaths: +4, morale: -3 },
        feedback: 'Fair-looking, but less effective in mass casualty medicine because urgency and survivability vary.',
      },
      {
        label: 'Treat only the loudest patients first',
        quality: 1,
        effects: { supplies: -10, wounded: +4, deaths: +7, morale: -9 },
        feedback: 'Bad triage. The loudest patients are not always the most urgent or most survivable.',
      },
    ],
  },
 ];

function generateVariantEvents() {
  const diseases = [
    {
      name: 'Dysentery',
      icon: '🤢',
      descriptor: 'severe dehydration and contaminated water',
      strong: 'Relocate waste trenches, boil water, and reorganize camp sanitation',
      mixed: 'Focus treatment only on the sickest patients',
      weak: 'Continue using the same contaminated water source',
      source: 'Dysentery spread through contaminated food and water in unsanitary camps.',
    },
    {
      name: 'Typhoid Fever',
      icon: '🥵',
      descriptor: 'high fevers and polluted wells',
      strong: 'Quarantine infected soldiers and secure cleaner water access',
      mixed: 'Use medicine without changing camp conditions',
      weak: 'Keep all soldiers in crowded shared quarters',
      source: 'Typhoid spread rapidly through polluted water and crowded camps.',
    },
    {
      name: 'Malaria',
      icon: '🦟',
      descriptor: 'mosquito-heavy swamp conditions',
      strong: 'Distribute quinine and relocate tents from swampy ground',
      mixed: 'Use quinine only after severe symptoms appear',
      weak: 'Ignore the fever wave and prioritize battle drills',
      source: 'Malaria weakened armies through recurring fever outbreaks.',
    },
    {
      name: 'Pneumonia',
      icon: '🫁',
      descriptor: 'cold rain, wet blankets, and exhaustion',
      strong: 'Improve warmth, nutrition, and tent ventilation',
      mixed: 'Treat only the worst coughing patients',
      weak: 'Keep exhausted soldiers outdoors overnight',
      source: 'Harsh weather and weakened immune systems contributed to pneumonia outbreaks.',
    },
    {
      name: 'Smallpox',
      icon: '🧬',
      descriptor: 'panic over contagious skin lesions',
      strong: 'Vaccinate exposed soldiers and isolate suspected cases',
      mixed: 'Isolate only visibly infected patients',
      weak: 'Dismiss the outbreak as harmless irritation',
      source: 'Vaccination and isolation were sometimes used to reduce smallpox spread.',
    },
  ];

  const settings = [
    'A supply camp near the river reports',
    'A crowded field hospital struggles with',
    'A train station medical post encounters',
    'A temporary pavilion ward faces',
    'A frontline recovery camp reports',
    'A transport ship hospital discovers',
    'An overcrowded surgical tent experiences',
    'A cavalry camp begins showing signs of',
  ];

  const strategyConflicts = [
    'You cannot solve every problem at once because staff, supplies, and sanitation are all strained.',
    'Several surgeons disagree on whether prevention or rapid treatment matters more.',
    'The camp commander wants soldiers returned to duty quickly despite rising infection rates.',
    'Rain and overcrowding are worsening recovery conditions throughout the hospital.',
    'Your nurses are exhausted, and transport wagons are delayed.',
  ];

  const generated = [];

  const criticalConflicts = [
    'A surgeon demands immediate amputation while another warns that the patient may survive without surgery.',
    'Rainwater has contaminated medical tents, but moving patients could worsen exposure and exhaustion.',
    'Your healthiest nurses are becoming sick after caring for contagious patients without separation.',
    'The hospital can either preserve supplies for future outbreaks or spend heavily now to stabilize current patients.',
    'Military officers pressure doctors to return recovering soldiers to battle before they are fully healed.',
    'A transport wagon carrying medicine has been delayed, forcing difficult prioritization decisions.',
    'Some doctors insist traditional heroic medicine should continue despite worsening mortality rates.',
    'The hospital kitchen cannot feed everyone adequately unless patient groups are prioritized.',
  ];

  diseases.forEach((disease, diseaseIndex) => {
    settings.forEach((setting, settingIndex) => {
      [...strategyConflicts, ...criticalConflicts].forEach((conflict, conflictIndex) => {
        generated.push({
          title: `${disease.name} Crisis #${settingIndex + 1}-${conflictIndex + 1}`,
          icon: disease.icon,
          type: 'Dynamic Medical Crisis',
          scene: `${setting} ${disease.descriptor}. ${conflict}`,
          sourceIdea: disease.source,
          options: shuffleArray([
            {
              label: disease.strong,
              quality: 3,
              effects: {
                sanitation: 10 + (diseaseIndex % 4),
                morale: 3,
                supplies: -8,
                disease: -7,
                survivors: 4,
                knowledge: 3,
              },
              feedback: 'Historically effective prevention and organization reduced disease spread even before modern medicine fully understood infection.',
            },
            {
              label: disease.mixed,
              quality: 2,
              effects: {
                supplies: -5,
                disease: -2,
                morale: -1,
                survivors: 2,
              },
              feedback: 'This partially addresses the problem, but it ignores larger environmental and organizational causes.',
            },
            {
              label: disease.weak,
              quality: 1,
              effects: {
                disease: 7,
                contagious: 4,
                morale: -5,
                deaths: 4,
              },
              feedback: 'Ignoring sanitation, overcrowding, or disease prevention usually allowed outbreaks to worsen rapidly.',
            },
            {
              label: 'Split resources evenly between all wards to avoid complaints',
              quality: 2,
              effects: {
                supplies: -10,
                morale: 2,
                survivors: 1,
                disease: 1,
              },
              feedback: 'Fairness can help morale, but spreading resources too thin may weaken overall effectiveness.',
            },
            {
              label: 'Preserve supplies for future emergencies instead of immediate action',
              quality: 2,
              effects: {
                supplies: 6,
                morale: -4,
                disease: 3,
              },
              feedback: 'Conserving supplies may help later, but delayed intervention often increased disease pressure.',
            },
          ]),
        });
      });
    });
  });

  for (let i = 0; i < 30; i += 1) {
    generated.push({
      title: `Ethics and Survival Crisis #${i + 1}`,
      icon: ['⚕️', '☁️', '🧪', '📜', '🕯️'][i % 5],
      type: 'Advanced Hospital Ethics',
      scene: `Resources are collapsing while infection rates continue rising. Doctors disagree on whether prevention, surgery, quarantine, or transportation should receive priority. Your decision will shape both survival rates and long-term hospital stability.`,
      sourceIdea: 'Civil War hospitals constantly balanced overcrowding, sanitation, transportation, disease control, and surgery under limited resources.',
      options: shuffleArray([
        {
          label: 'Redirect resources into long-term sanitation and disease prevention systems',
          quality: 3,
          effects: {
            sanitation: 12,
            disease: -8,
            morale: 3,
            supplies: -10,
            survivors: 4,
            knowledge: 4,
          },
          feedback: 'Preventive organization often saved more lives over time than reacting only after outbreaks worsened.',
        },
        {
          label: 'Focus entirely on immediate battlefield surgeries to reduce visible suffering',
          quality: 2,
          effects: {
            wounded: -7,
            disease: 5,
            supplies: -12,
            survivors: 3,
          },
          feedback: 'Surgery helped many soldiers, but ignoring disease control allowed hospitals to become overwhelmed later.',
        },
        {
          label: 'Preserve supplies and avoid making major decisions until conditions become clearer',
          quality: 1,
          effects: {
            supplies: 6,
            morale: -6,
            disease: 8,
            deaths: 4,
          },
          feedback: 'Delaying action during outbreaks often increased mortality and overcrowding pressure.',
        },
        {
          label: 'Move contagious patients away from recovering wards despite transportation risk',
          quality: 3,
          effects: {
            contagious: -10,
            transport: -5,
            sanitation: 5,
            survivors: 5,
            morale: -1,
          },
          feedback: 'Separating contagious patients reduced spread even when transportation itself carried risks.',
        },
        {
          label: 'Reduce food portions temporarily so medicine and bandages last longer',
          quality: 2,
          effects: {
            supplies: 8,
            morale: -8,
            recovering: -4,
            disease: 3,
          },
          feedback: 'Resource conservation can help temporarily, but weakened nutrition harms recovery and morale.',
        },
      ]),
    });
  }

  return generated;
}

const eventDeck = shuffleArray([...eventTemplates, ...generateVariantEvents()]);

const upgrades = [
  {
    key: 'pavilion',
    name: 'Pavilion Ward',
    icon: '🏥',
    cost: { supplies: 18, staff: 8 },
    desc: 'Adds airflow and spacing to reduce disease spread each day.',
  },
  {
    key: 'ambulance',
    name: 'Ambulance Corps',
    icon: '🚑',
    cost: { supplies: 14, staff: 6 },
    desc: 'Improves transport and lowers deaths from delayed treatment.',
  },
  {
    key: 'isolation',
    name: 'Isolation Ward',
    icon: '🚪',
    cost: { supplies: 12, staff: 7 },
    desc: 'Separates contagious patients from recovering patients.',
  },
  {
    key: 'supplyDepot',
    name: 'Supply Depot',
    icon: '📦',
    cost: { supplies: 10, staff: 5 },
    desc: 'Improves daily supply recovery and hospital stability.',
  },
  {
    key: 'recordkeeping',
    name: 'Patient Records',
    icon: '📋',
    cost: { supplies: 8, staff: 5 },
    desc: 'Improves medical knowledge and survival from organized care.',
  },
  {
    key: 'cleanWater',
    name: 'Clean Water System',
    icon: '💧',
    cost: { supplies: 20, staff: 8 },
    desc: 'Reduces dysentery and typhoid pressure from contaminated water.',
  },
  {
    key: 'nursingRotation',
    name: 'Nursing Rotation',
    icon: '🧑‍⚕️',
    cost: { supplies: 12, staff: 10 },
    desc: 'Improves morale and recovery by organizing daily care.',
  },
  {
    key: 'pharmacy',
    name: 'Field Pharmacy',
    icon: '⚗️',
    cost: { supplies: 16, staff: 6 },
    desc: 'Improves medicine allocation and reduces waste.',
  },
];

function applyEffects(game, effects) {
  const next = structuredClone(game);
  const patientKeys = ['disease', 'wounded', 'contagious', 'recovering'];

  Object.entries(effects).forEach(([key, value]) => {
    if (patientKeys.includes(key)) next.patients[key] = Math.max(0, next.patients[key] + value);
    else if (key in next) {
      if (key === 'deaths' || key === 'survivors' || key === 'reputation') next[key] = Math.max(0, next[key] + value);
      else next[key] = clamp(next[key] + value);
    }
  });

  return next;
}

function meterColor(value) {
  if (value >= 70) return 'bg-gradient-to-r from-[#b8f7d4] to-[#bdebd1]';
  if (value >= 40) return 'bg-gradient-to-r from-[#fff4c7] to-[#d9edff]';
  return 'bg-gradient-to-r from-[#ffd6df] to-[#d9eaff]';
}

function StatMeter({ label, value, icon }) {
  return (
    <div className="rounded-[2rem] bg-gradient-to-br from-white/70 to-[#efe6ff]/70 border border-white/50 p-4 shadow-[0_16px_45px_rgba(200,220,255,0.13)] hover:scale-[1.02] transition duration-300">
      <div className="flex items-center justify-between mb-2">
        <span className="text-sm tracking-wide text-[#8f7bb0]/80">{icon} {label}</span>
        <span className="font-bold text-[#5b6b88]">{value}</span>
      </div>
      <div className="h-3 rounded-full bg-[#e6ddf7] overflow-hidden">
        <div className={`h-full ${meterColor(value)}`} style={{ width: `${clamp(value)}%` }} />
      </div>
    </div>
  );
}

function DiseaseBar({ name, value, icon }) {
  return (
    <div className="mb-3">
      <div className="flex justify-between items-center mb-1 text-sm">
        <span className="font-bold text-[#7a88a3] flex items-center gap-2">{icon} {name}</span>
        <span className="text-[#5b6b88]">{value}</span>
      </div>
      <div className="h-2 rounded-full bg-[#e6ddf7] overflow-hidden">
        <div className="h-full bg-gradient-to-r from-[#b9dcff] to-[#bdebd1]" style={{ width: `${Math.min(100, value * 4)}%` }} />
      </div>
    </div>
  );
}

function PatientTile({ label, value, icon, detail }) {
  return (
    <div className="rounded-[2rem] bg-gradient-to-br from-[#f8fbff] to-[#f2fff8] border border-white/70 p-5 hover:from-[#eef7ff] hover:to-[#edfff6] transition duration-300 hover:scale-[1.02] shadow-lg">
      <div className="text-4xl mb-3 drop-shadow-sm">{icon}</div>
      <div className="text-2xl font-medium tracking-[-0.02em] text-[#5b6b88]">{value}</div>
      <div className="font-bold text-[#7a88a3]">{label}</div>
      <div className="text-xs text-[#7a88a3]/60 mt-1 leading-relaxed">{detail}</div>
    </div>
  );
}

function ChoiceBadge({ quality }) {
  const label = quality === 3 ? 'Strong' : quality === 2 ? 'Mixed' : 'Dangerous';
  const className = quality === 3 ? 'bg-emerald-300 text-[#5b6b88]' : quality === 2 ? 'bg-amber-200 text-[#5b6b88]' : 'bg-rose-300 text-[#5b6b88]';
  return <span className={`rounded-full px-3 py-1 text-xs font-medium ${className}`}>{label}</span>;
}

export default function CivilWarMedicineGame() {
  const [game, setGame] = useState(() => makeInitialGame());
  const [eventIndex, setEventIndex] = useState(0);
  const [selectedCard, setSelectedCard] = useState(0);
  const [eventOrder, setEventOrder] = useState(() => shuffleArray(eventDeck.map((_, index) => index)));
  const [optionOrder, setOptionOrder] = useState(() => shuffleArray([0, 1, 2, 3, 4]));
  const [showBadges, setShowBadges] = useState(false);

  const currentEvent = eventDeck[eventOrder[eventIndex % eventOrder.length]];

  const hardMode = currentEvent.type === 'Mass Casualty Triage' || currentEvent.type === 'Resource Allocation' || currentEvent.type === 'Infection Theory';
  const currentOptions = optionOrder
    .filter((index) => index < currentEvent.options.length)
    .map((index) => currentEvent.options[index]);

  const totalPatients = game.patients.disease + game.patients.wounded + game.patients.contagious + game.patients.recovering;
  const score = useMemo(() => {
    const earned = (game.survivors * 4) + (game.reputation * 3) + (game.streak * 6) - (game.deaths * 5);
    return Math.max(0, earned);
  }, [game]);
  const gameOver = game.day > 20 || game.sanitation <= -5 || game.supplies <= -5 || game.staff <= -5 || game.morale <= -5;

  function chooseOption(option) {
    if (gameOver) return;
    let next = applyEffects(game, option.effects);
    next.phase = 'result';
    next.streak = option.quality === 3 ? next.streak + 1 : option.quality === 1 ? 0 : Math.max(0, next.streak - 1);
    next.learned = [option.feedback, ...next.learned].slice(0, 6);
    next.log = [`Day ${game.day}: ${option.label} (${option.quality === 3 ? 'strong' : option.quality === 2 ? 'mixed' : 'dangerous'} choice)`, ...next.log].slice(0, 10);
    setShowBadges(true);
    setGame(next);
  }

  function nextDay() {
    if (gameOver) return;

    let next = structuredClone(game);
    next.day += 1;
    next.phase = 'briefing';

    const diseasePressure = Math.max(2, Math.round((100 - next.sanitation) / 14));
    const overcrowdingPressure = Math.max(0, Math.round((totalPatients - 65) / 10));
    const transportHelp = next.upgrades.ambulance ? 4 : 0;
    const pavilionHelp = next.upgrades.pavilion ? 4 : 0;
    const isolationHelp = next.upgrades.isolation ? 6 : 0;
    const recordsHelp = next.upgrades.recordkeeping ? 3 : 0;
    const depotHelp = next.upgrades.supplyDepot ? 8 : 3;
    const waterHelp = next.upgrades.cleanWater ? 5 : 0;
    const nursingHelp = next.upgrades.nursingRotation ? 5 : 0;
    const pharmacyHelp = next.upgrades.pharmacy ? 3 : 0;

    const newDisease = Math.max(0, diseasePressure + overcrowdingPressure - pavilionHelp - isolationHelp - waterHelp);
    const preventableDeaths = Math.max(0, Math.round((next.patients.contagious + next.patients.wounded + next.patients.disease) / 28) - transportHelp - recordsHelp - nursingHelp);
    const recovered = Math.max(2, Math.round((next.patients.recovering + next.staff / 9 + next.knowledge / 14 + nursingHelp + pharmacyHelp) / 2.5));
    const newWounded = next.day % 4 === 0 ? 10 : next.day % 5 === 0 ? 7 : 2;

    next.patients.disease += newDisease;

    next.diseaseBreakdown.dysentery += Math.max(0, Math.round(newDisease / 4));
    next.diseaseBreakdown.typhoid += Math.max(0, Math.round(newDisease / 5));
    next.diseaseBreakdown.malaria += next.day % 3 === 0 ? 2 : 1;
    next.diseaseBreakdown.pneumonia += next.day % 4 === 0 ? 2 : 0;
    next.diseaseBreakdown.smallpox += next.day % 6 === 0 ? 1 : 0;
    next.diseaseBreakdown.measles += next.day % 5 === 0 ? 1 : 0;
    next.patients.wounded += newWounded;
    next.patients.contagious = Math.max(0, next.patients.contagious + Math.round(newDisease / 2) - isolationHelp);
    next.patients.recovering = Math.max(0, next.patients.recovering - recovered + Math.round(next.staff / 22));
    next.survivors += recovered;
    next.deaths += preventableDeaths;
    next.supplies = clamp(next.supplies + depotHelp - Math.round(totalPatients / 28));
    next.staff = clamp(next.staff + (next.day % 6 === 0 ? 5 : 2) - Math.round(totalPatients / 90));
    next.sanitation = clamp(next.sanitation - Math.max(2, Math.round(totalPatients / 28)) + pavilionHelp + waterHelp);
    next.morale = clamp(next.morale - preventableDeaths + (recovered > 5 ? 5 : 1) + (next.upgrades.nursingRotation ? 3 : 0));
    next.knowledge = clamp(next.knowledge + recordsHelp + 1);
    next.log = [`Day ${next.day}: Disease pressure +${newDisease}, new wounded +${newWounded}, recovered ${recovered}, deaths ${preventableDeaths}.`, ...next.log].slice(0, 10);

    setEventIndex((i) => {
      const nextIndex = i + 1;
      if (nextIndex % eventOrder.length === 0) setEventOrder(shuffleArray(eventDeck.map((_, index) => index)));
      return nextIndex;
    });
    setOptionOrder(shuffleArray([0, 1, 2, 3, 4]));
    setShowBadges(false);
    setGame(next);
  }

  function buyUpgrade(upgrade) {
    if (game.upgrades[upgrade.key] || gameOver) return;
    if (game.supplies < upgrade.cost.supplies || game.staff < upgrade.cost.staff) return;

    const next = structuredClone(game);
    next.supplies -= upgrade.cost.supplies;
    next.staff -= upgrade.cost.staff;
    next.upgrades[upgrade.key] = true;
    next.knowledge = clamp(next.knowledge + 5);
    next.log = [`Built upgrade: ${upgrade.name}.`, ...next.log].slice(0, 10);
    next.learned = [`${upgrade.name}: ${upgrade.desc}`, ...next.learned].slice(0, 6);
    setGame(next);
  }

  function restart() {
    setGame(makeInitialGame());
    setEventIndex(0);
    setSelectedCard(0);
    setEventOrder(shuffleArray(eventDeck.map((_, index) => index)));
    setOptionOrder(shuffleArray([0, 1, 2, 3, 4]));
    setShowBadges(false);
  }

  return (
    <main className="min-h-screen bg-[radial-gradient(circle_at_top,#f7fbff,#f9f4ff_30%,#f3fff8_68%,#ffffff)] text-[#5b6b88] p-4 md:p-8 font-['Inter'] overflow-hidden relative">
      <div className="absolute inset-0 opacity-10 pointer-events-none bg-gradient-to-br from-[#dbeafe]/20 via-[#f5e8ff]/10 to-[#dcfce7]/20" />
      <div className="absolute top-0 left-0 w-full h-96 bg-gradient-to-b from-[#f5e8ff]/25 to-transparent pointer-events-none" />
      <section className="max-w-7xl mx-auto relative z-10">
        <div className="mb-8 rounded-[2.5rem] overflow-hidden border border-white/70 bg-white/50 shadow-[0_30px_80px_rgba(180,200,255,0.18)]">
          <div className="relative h-[280px] md:h-[360px] overflow-hidden">
            <div className="absolute inset-0 bg-[radial-gradient(circle_at_20%_30%,rgba(255,255,255,0.8),transparent_30%),radial-gradient(circle_at_80%_20%,rgba(255,220,255,0.55),transparent_25%),radial-gradient(circle_at_70%_80%,rgba(220,240,255,0.5),transparent_30%),linear-gradient(135deg,#f4f7ff,#eef8ff,#eafff5)]" />
            <div className="absolute inset-0 bg-gradient-to-r from-[#fbfdff]/90 via-[#eff7ff]/70 to-transparent" />
            <div className="relative z-10 p-8 md:p-12 flex flex-col justify-end h-full">
              <div className="uppercase tracking-[0.4em] text-xs text-[#9db4d4]/80 font-medium mb-4">Interactive Civil War Medical Simulation</div>
              <h1 className="text-5xl md:text-7xl font-light tracking-[-0.04em] leading-[0.9] mb-4 max-w-4xl">
                Civil War Medicine:<br/>Field Hospital Simulator
              </h1>
              <p className="text-lg md:text-xl text-[#7a88a3]/80 max-w-3xl leading-relaxed">
                Manage a soft historical strategy game inspired by Civil War medical crises, where disease outbreaks, surgery, sanitation, supplies, and survival decisions all interact.
              </p>
            </div>
          </div>
        </div>
        <div className="grid lg:grid-cols-[1.1fr_.9fr] gap-6 items-stretch mb-6">
          <div className="rounded-[2.5rem] bg-white/70 border border-white/70 shadow-[0_20px_60px_rgba(190,210,255,0.14)] p-6 md:p-8 overflow-hidden relative">
            <div className="absolute right-6 top-6 text-8xl opacity-20 animate-[pulse_6s_ease-in-out_infinite]">🩺</div>
            <p className="uppercase tracking-[0.3em] text-xs text-[#9db4d4]/80 font-bold mb-3">Historical Medical Strategy</p>
            <h1 className="text-4xl md:text-6xl font-light tracking-[-0.03em] leading-tight mb-4">Civil War Field Hospital</h1>
            <p className="text-lg text-[#7a88a3]/85 leading-relaxed max-w-3xl">
              Guide a Civil War field hospital through outbreaks, surgeries, overcrowding, sanitation crises, and difficult medical decisions while trying to keep patients and staff alive. Survival is difficult but fully possible with strong long-term planning, balanced resource management, and smart disease prevention.
            </p>
            <div className="flex flex-wrap gap-3 mt-6">
              <span className="px-4 py-2 rounded-full bg-gradient-to-r from-[#f8fbff] to-[#f7f4ff] text-[#5b6b88] font-bold">Day {Math.min(game.day, 20)}/20</span>
              <span className="px-4 py-2 rounded-full bg-white/55 border border-white/70">Score: {score}</span>
              <span className="px-4 py-2 rounded-full bg-white/55 border border-white/70">Patients: {totalPatients}</span>
              <span className="px-4 py-2 rounded-full bg-white/55 border border-white/70">Best-decision streak: {game.streak}</span>
            </div>
          </div>

          <div className="rounded-[2.5rem] bg-white/55 border border-white/70 p-5 shadow-[0_20px_60px_rgba(190,210,255,0.14)]">
            <h2 className="text-3xl font-medium tracking-[-0.02em] mb-4 text-[#5e6f90]">Medical Knowledge Archive</h2>
            <div className="grid grid-cols-5 gap-2 mb-4">
              {historicalCards.map((card, index) => (
                <button key={card.title} onClick={() => setSelectedCard(index)} className={`rounded-[1.5rem] p-3 text-2xl border ${selectedCard === index ? 'bg-gradient-to-r from-[#f8fbff] to-[#f7f4ff] text-[#5b6b88] border-[#d7e8ff]' : 'bg-white/75 border-white/70'}`}>
                  {card.icon}
                </button>
              ))}
            </div>
            <div className="rounded-[1.5rem] bg-white/75 border border-white/70 p-5 min-h-[190px]">
              <div className="text-4xl mb-3">{historicalCards[selectedCard].icon}</div>
              <h3 className="text-xl font-medium mb-2">{historicalCards[selectedCard].title}</h3>
              <p className="text-[#7a88a3]/80 leading-relaxed">{historicalCards[selectedCard].text}</p>
            </div>
          </div>
        </div>

        <div className="grid md:grid-cols-5 gap-3 mb-6">
          <StatMeter label="Sanitation" value={game.sanitation} icon="🧼" />
          <StatMeter label="Supplies" value={game.supplies} icon="📦" />
          <StatMeter label="Staff" value={game.staff} icon="🧑‍⚕️" />
          <StatMeter label="Morale" value={game.morale} icon="🕯️" />
          <StatMeter label="Medical Knowledge" value={game.knowledge} icon="📚" />
        </div>

        <div className="grid lg:grid-cols-[.8fr_1.2fr] gap-6 mb-6">
          <div className="rounded-[2.5rem] bg-white/70 border border-white/70 p-5 shadow-[0_16px_45px_rgba(200,220,255,0.13)]">
            <h2 className="text-2xl font-medium tracking-[-0.02em] mb-4">Hospital Systems Overview</h2>
            <div className="grid grid-cols-2 gap-3">
              <PatientTile label="Disease Ward" value={game.patients.disease} icon="🤒" detail="Dysentery, typhoid, malaria, pneumonia, measles, smallpox" />
              <PatientTile label="Wounded Ward" value={game.patients.wounded} icon="🩹" detail="Battle wounds, shattered bones, surgical emergencies" />
              <PatientTile label="Contagious" value={game.patients.contagious} icon="🦠" detail="Patients who worsen outbreaks if not separated" />
              <PatientTile label="Recovering" value={game.patients.recovering} icon="🛏️" detail="Stable patients who may survive if care continues" />
            </div>
            <div className="mt-4 rounded-[1.5rem] bg-white/45 p-4 border border-white/70 mb-4">
              <h3 className="font-medium text-lg mb-3">Disease Spread Visualizer</h3>
              <DiseaseBar name="Dysentery" value={game.diseaseBreakdown.dysentery} icon={diseaseIcons.dysentery} />
              <DiseaseBar name="Typhoid" value={game.diseaseBreakdown.typhoid} icon={diseaseIcons.typhoid} />
              <DiseaseBar name="Malaria" value={game.diseaseBreakdown.malaria} icon={diseaseIcons.malaria} />
              <DiseaseBar name="Pneumonia" value={game.diseaseBreakdown.pneumonia} icon={diseaseIcons.pneumonia} />
              <DiseaseBar name="Smallpox" value={game.diseaseBreakdown.smallpox} icon={diseaseIcons.smallpox} />
              <DiseaseBar name="Measles" value={game.diseaseBreakdown.measles} icon={diseaseIcons.measles} />
            </div>

            <div className="mt-4 rounded-[1.5rem] bg-white/45 p-4 border border-white/70">
              <div className="flex justify-between"><span>Survivors</span><b>{game.survivors}</b></div>
              <div className="flex justify-between"><span>Deaths</span><b>{game.deaths}</b></div>
              <div className="flex justify-between"><span>Transport Capacity</span><b>{game.transport}</b></div>
            </div>
          </div>

          <div className="rounded-[2.5rem] bg-white/75 border border-white/70 p-5 md:p-6 shadow-[0_16px_45px_rgba(200,220,255,0.13)]">
            {gameOver ? (
              <div className="min-h-[420px] flex flex-col justify-center">
                <div className="text-7xl mb-4">{game.day > 20 ? '🏆' : '⚠️'}</div>
                <h2 className="text-4xl font-medium mb-3">{game.day > 20 ? 'Simulation Complete' : 'Hospital Collapse'}</h2>
                <p className="text-[#7a88a3]/85 leading-relaxed mb-5">
                  Final score: {score}. Survivors: {game.survivors}. Deaths: {game.deaths}. Knowledge: {game.knowledge}. The best runs balance disease prevention, surgery, hospital organization, transport, nursing, and supply use.
                </p>
                <button onClick={restart} className="rounded-[1.5rem] bg-gradient-to-r from-[#f8fbff] to-[#f7f4ff] text-[#5b6b88] font-medium px-6 py-4 w-fit">Restart Simulation</button>
              </div>
            ) : game.phase === 'result' ? (
              <div>
                <p className="uppercase tracking-[0.25em] text-xs text-[#9db4d4]/75 font-bold mb-2">Historical Feedback</p>
                <h2 className="text-3xl font-medium tracking-[-0.02em] mb-4">What Your Decision Shows</h2>
                <div className="rounded-[2rem] bg-white/45 border border-white/70 p-5 mb-5 leading-relaxed text-[#7a88a3]/85">
                  {game.learned[0]}
                </div>
                <button onClick={nextDay} className="rounded-[1.5rem] bg-gradient-to-r from-[#f8fbff] to-[#f7f4ff] hover:bg-white text-[#5b6b88] font-medium px-6 py-4 transition">Advance to Next Day</button>
              </div>
            ) : (
              <div>
                <div className="flex items-start gap-4 mb-4">
                  <div className="text-6xl">{currentEvent.icon}</div>
                  <div>
                    <p className="uppercase tracking-[0.25em] text-xs text-[#9db4d4]/75 font-bold mb-2">{currentEvent.type}</p>
                    <h2 className="text-3xl md:text-4xl font-medium">{currentEvent.title}</h2>
                  </div>
                </div>
                <p className="text-lg text-[#7a88a3]/85 leading-relaxed mb-4">{currentEvent.scene}</p>
                <div className="rounded-[1.5rem] bg-white/45 border border-white/70 p-4 mb-5 text-sm text-[#7a88a3]/80">
                  {hardMode && (
                    <div className="mb-3 rounded-xl bg-[#ffe1f2]/80 border border-[#b9dcff]/60 p-3 text-[#8b4f76]">
                      <div className="font-medium mb-1">Hard Decision Scenario</div>
                      <div className="text-xs leading-relaxed">In this event, every option has major tradeoffs. The historically best answer may still cause deaths, morale loss, or supply collapse.</div>
                    </div>
                  )}
                  <b className="text-[#5b6b88]">Historical connection:</b> {currentEvent.sourceIdea}
                </div>
                <div className="grid gap-3">
                  <div className="grid grid-cols-5 gap-2 mb-2">
                    <div className="rounded-xl bg-white/70 p-3 text-center border border-white/70">
                      <div className="text-2xl">🦠</div>
                      <div className="text-xs mt-1">Disease Risk</div>
                      <div className="font-medium text-lg">{game.patients.disease > 55 ? 'HIGH' : game.patients.disease > 30 ? 'MED' : 'LOW'}</div>
                    </div>
                    <div className="rounded-xl bg-white/70 p-3 text-center border border-white/70">
                      <div className="text-2xl">📦</div>
                      <div className="text-xs mt-1">Supplies</div>
                      <div className="font-medium text-lg">{game.supplies < 30 ? 'LOW' : game.supplies < 60 ? 'MID' : 'GOOD'}</div>
                    </div>
                    <div className="rounded-xl bg-white/70 p-3 text-center border border-white/70">
                      <div className="text-2xl">🧑‍⚕️</div>
                      <div className="text-xs mt-1">Staff</div>
                      <div className="font-medium text-lg">{game.staff < 25 ? 'TIRED' : game.staff < 55 ? 'STRAINED' : 'READY'}</div>
                    </div>
                    <div className="rounded-xl bg-white/70 p-3 text-center border border-white/70">
                      <div className="text-2xl">⚰️</div>
                      <div className="text-xs mt-1">Deaths</div>
                      <div className="font-medium text-lg">{game.deaths}</div>
                    </div>
                    <div className="rounded-xl bg-white/70 p-3 text-center border border-white/70">
                      <div className="text-2xl">🏆</div>
                      <div className="text-xs mt-1">Score</div>
                      <div className="font-medium text-lg">{score}</div>
                    </div>
                  </div>
                  <div className="rounded-[1.5rem] bg-white/70 border border-white/70 p-4 mb-2">
                    <div className="text-sm text-[#7a88a3]/70 leading-relaxed">
                      <span className="font-medium text-[#5b6b88]">Hospital pressure report:</span>
                      {' '}Disease load is {game.patients.disease > 60 ? 'critical' : game.patients.disease > 35 ? 'high' : 'moderate'}, sanitation is {game.sanitation < 35 ? 'poor' : game.sanitation < 65 ? 'unstable' : 'stable'}, and morale is {game.morale < 35 ? 'collapsing' : game.morale < 65 ? 'strained' : 'holding'}.
                    </div>
                  </div>
                  {currentOptions.map((option) => (
                    <button key={option.label} onClick={() => chooseOption(option)} className="text-left group relative overflow-hidden rounded-[2rem] bg-gradient-to-br from-[#ffffff] via-[#f8f6ff] to-[#f2fbff] hover:from-[#fcfbff] hover:to-[#eefaff] border border-white/70 p-5 transition duration-300 hover:scale-[1.02] hover:-translate-y-1 hover:shadow-[0_10px_40px_rgba(190,220,255,0.35)]">
                      <div className="flex items-center justify-between gap-3 mb-1">
                        <div className="font-medium text-lg">{option.label}</div>
                        {showBadges && <ChoiceBadge quality={option.quality} />}
                      </div>
                      <div className="text-xs text-[#7a88a3]/55">Every answer changes the hospital differently. Some improve survival short-term but damage sanitation, morale, or future stability.</div>
                    </button>
                  ))}
                </div>
              </div>
            )}
          </div>
        </div>

        <div className="grid lg:grid-cols-2 gap-6">
          <div className="rounded-[2.5rem] bg-white/55 border border-white/70 p-5 shadow-[0_16px_45px_rgba(200,220,255,0.13)]">
            <h2 className="text-3xl font-medium tracking-[-0.02em] mb-2 text-[#5e6f90]">Build Hospital Improvements</h2>
            <p className="text-sm text-[#7a88a3]/55 mb-4">Expand your hospital with sanitation systems, organized transport, nursing rotations, and medical infrastructure upgrades.</p>
            <div className="grid sm:grid-cols-2 gap-3">
              {upgrades.map((upgrade) => {
                const owned = game.upgrades[upgrade.key];
                const canBuy = game.supplies >= upgrade.cost.supplies && game.staff >= upgrade.cost.staff && !owned && !gameOver;
                return (
                  <button key={upgrade.key} onClick={() => buyUpgrade(upgrade)} className={`text-left rounded-[1.5rem] p-4 border transition ${owned ? 'bg-[#e1fff0]/80 border-[#b9f5d0]/70' : canBuy ? 'bg-white/75 hover:bg-[#f7e9ff] border-white/70' : 'bg-white/30 border-white/70 opacity-60'}`}>
                    <div className="text-4xl mb-3 drop-shadow-sm">{upgrade.icon}</div>
                    <div className="font-medium text-lg">{upgrade.name}</div>
                    <div className="text-xs text-[#7a88a3]/65 my-2 leading-relaxed">{upgrade.desc}</div>
                    <div className="text-xs">Cost: {upgrade.cost.supplies} supplies, {upgrade.cost.staff} staff {owned ? '— Built' : ''}</div>
                  </button>
                );
              })}
            </div>
          </div>

          <div className="rounded-[2.5rem] bg-white/55 border border-white/70 p-5 shadow-[0_16px_45px_rgba(200,220,255,0.13)]">
            <h2 className="text-3xl font-medium tracking-[-0.02em] mb-2 text-[#5e6f90]">Decision Log</h2>
            <p className="text-sm text-[#7a88a3]/55 mb-4">Your previous medical decisions, organizational choices, and crisis responses are recorded here.</p>
            <div className="space-y-2 max-h-[520px] overflow-auto pr-2">
              {game.log.map((entry, index) => (
                <div key={`${entry}-${index}`} className="rounded-[1.5rem] bg-white/75 border border-white/70 p-3 text-sm text-[#7a88a3]/80">{entry}</div>
              ))}
            </div>
          </div>
        </div>
      </section>
    </main>
  );
}

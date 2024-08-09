% Existing code
clear all;
close all;

% Initialize the IVI configuration store
configStore = iviconfigurationstore;

% Create a device object for the NI PXI-5105
dev = ividev('IviScope', 'PXI-5105');

reset(dev);
autoSetup(dev);

Range = 10;
Offset = 0;
ProbeAttenuation = 1;

numSamples = 1024;
TimeOut = 1000; % millisec

% Fetch the waveform data
initiateAcquisition(dev);
samples = fetchWaveform(dev, '0', numSamples);

% Calculate the average of samples
averageSamples = mean(samples);

% Plot the waveform data
t = (0:size(samples, 2) - 1);
plot(t, samples, 'DisplayName', 'Channel 0');
hold on;
plot(t, averageSamples * ones(1, size(samples, 2)), 'DisplayName', 'Average', 'LineStyle', '--');
grid on;
xlabel('Time (s)');
ylabel('Volts (V)');
legend;
title('Waveform from NI PXI-5105');

% Clean up
clear dev;
